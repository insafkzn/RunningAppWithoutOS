Теперь скомпилируем код в бинарный файл следующими командами:
    as -o loader.o loader.s
    gcc -Iinclude -Wall -fno-builtin -nostdinc -nostdlib -o kernel.o -c kernel.c
    gcc -Iinclude -Wall -fno-builtin -nostdinc -nostdlib -o printf.o -c common/printf.c
    gcc -Iinclude -Wall -fno-builtin -nostdinc -nostdlib -o screen.o -c common/screen.c
    ld -T linker.ld -o kernel.bin kernel.o screen.o printf.o loader.o

С помощью objdump’а рассмотрим, как выглядит образ ядра после линковки:
    objdump -ph ./kernel.bin


Скопировать в папку grub несколько файлов:
cp /usr/lib/grub/i386-pc/stage1 ./grub/
cp /usr/lib/grub/i386-pc/stage2 ./grub/
cp /usr/lib/grub/i386-pc/fat_stage1_5 ./grub/