# Step 1 - Get the GNU Toolchain

The Raspberry Pi only knows how to run instructions that are written as binary codes, but we are definitely not going to be writing instructions in binary. So we need a program that can translate from languages such as assembly and C and create files that our CPU can use. This is the job of the compiler, linker, and assembler. However, if you already have one of these set up on your machine, it probably won't make executable code for the Pi, but rather whatever machine you're using. It will probably also make assumptions about what sorts of fancy libraries you have installed.

So, the first step is to download a "bare metal" compiler that knows it's talking to the raspberry pi's CPU and also that it cannot rely on any nice libraries. Such a compiler is called a "cross compiler" since it is not making executables for its native hardware. Lucky for us, we can visit https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-a/downloads to find some ready-to-go toolchains. I'm developing the OS on Windows right now, so I scroll down to the "windows hosted" cross compilers and download the "AArch64 bare-metal target" file ending in ".xz". You can also download the ".asc" file that contains an MD5 checksum.

Create a folder called 'gnu-tools' somewhere convenient and move the xz file into it. Run `md5sum <file>` and look at the random-looking string you see there. Compare it to the number you see in the 'asc' file and make sure it matches. Now, decompress the 'xz' file with the command `tar xvf <file>`. You should see a big pile of filenames getting dumped to the screen. 

Look inside 'gnu-tools/bin'. You will find several executables that form the various programs you need to convert your "human" programs into "machine" programs and create an executable.