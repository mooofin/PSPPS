# PSPPS - A PlayStation Portable Emulator in Rust

PSPPS is a work-in-progress emulator for the Sony PlayStation Portable (PSP), written in Rust. This project aims to explore the architecture of the PSP and the challenges of hardware emulation 

## Project Philosophy

The development of this emulator is following a structured, incremental approach, inspired by the journey of successful emulators like PPSSPP. The focus is on building a solid foundation and gradually implementing features, rather than aiming for full game compatibility from day one.

## The Journey So Far (And Where We're Going)

This project is a long-term endeavor. Here is a rough outline of the development roadmap, broken down into major milestones.

### **Step 0: Research**
The initial phase involves deep-diving into the PSP's architecture. This means spending significant time with:
*   The [PPSSPP source code](https://github.com/hrydgard/ppsspp) to understand existing implementations.
*   The [PSPVitawiki](https://www.psdevwiki.com/psp/) for hardware details and specifications.
*   MIPS architecture manuals to understand the R4000-based CPU at the core of the PSP.

### **Step 1: The CPU**
The heart of the emulator is the MIPS instruction decoder. The initial goal is to create a simple program that can:
1.  Load a snippet of MIPS machine code into a byte array.
2.  Execute a few simple instructions (like `ADD`, `SUB`, `ADDI`).
3.  Print the state of the CPU registers to the console after each instruction.

*Status: Basic CPU structure is in place (`src/cpu/`).*

### **Step 2: Memory**
With a basic CPU, the next step is to implement a memory bus that the CPU can interact with. This allows the CPU to read instructions and data from a simulated memory space.

*Status: Initial memory module created (`src/memory/`).*

### **Step 3: Kernel Stubs**
The PSP's operating system, referred to as the "Kernel," provides essential services to games and applications. We will begin by implementing the most critical functions for threading and logging. When the emulated program calls a kernel function that hasn't been implemented yet, the emulator will print a message like `Unimplemented syscall: sceKernelSleepThread`.

*Status: Kernel module and syscall stubs are being developed (`src/kernel/`).*

### **Step 4: Loading an Executable**
To run actual PSP programs, we need to load them. This step involves implementing the logic to parse an ISO file and load the `EBOOT.BIN` executable into the emulated memory.

*Status: Loader module is being designed (`src/loader/`).*

### **Step 5: First Graphics**
This is a massive milestone. The goal is to get the first visual output from a homebrew program. This involves:
1.  Setting up a window using a library like `winit`.
2.  Implementing the most basic GPU commands to clear the screen to a specific color.

*Status: GPU module is planned (`src/gpu/`).*

### **Step 6: Iterate for 
From here, the journey is one of continuous, iterative development. This will involve:
*   Implementing more and more MIPS instructions.
*   Fleshing out the vast library of kernel functions.
*   Expanding the GPU command implementation to support more complex graphics.
*   Fixing the thousands of bugs that will inevitably appear along the way.

## Getting Started

This project is in its very early stages dont shame 

```bash
# Clone the repository
git clone https://github.com/your-username/PSPPS.git
cd PSPPS

# Build the project
cargo build

# Run the project
cargo run
```

## Contributing

Contributions are welcome! If you are interested in helping with the development of PSPPS, please feel free to fork the repository, make your changes, and submit a pull request.



## Resources

*   [PPSSPP Source Code](https://github.com/hrydgard/ppsspp)
*   [PSPVitawiki](https://www.psdevwiki.com/psp/)
*   [MIPS Architecture Manuals](https://www.google.com/search?q=mips+architecture+manual)
