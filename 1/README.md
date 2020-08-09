Let's test the compiler to make sure everything works OK, and to get some understanding about what happens.

First, copy or type the start.s file.

# Making an ELF file
Now enter `../../gnu-tools/bin/aarch64-none-elf-gcc -nostartfiles -mcpu=cortex-a72 start.s -o kernel8.elf` into a command line. Note that `../../gnu-tools/` is just whatever directory you placed your gnu-tools directory. 

This takes the assembly file start.s that we wrote and converts it into an elf file, which is a format almost ready to be executed by a machine.

How about the options?
* `nostartfiles` tells the compiler standard system startup files do not exist
* `mcpu=cortex-a72` tells the compiler exactly what processor it's expected
* `o` specifies the output file name

# Making the image

If you recall, your raspberry pi os had several files called 'kernel.img' and 'kernel8.img', and others. The last step is to convert our elf file into one of these. Use

`../../gnu-tools/bin/aarch64-none-elf-objcopy kernel8.elf -O binary kernel8.img`

# Conclusion

If all that works, you probably have set up your gcc stuff right! I wouldn't suggest doing anything with that kernel file just yet, since it doesn't really do anything...