# C/C++ File Extensions Reference — Part 1
### Source Files, Headers, Templates, Modules & Preprocessor Files

This part covers the files you typically write or that the compiler front end consumes before code generation.

| Extension        | Category            | Used For                        | Common Toolchains     | Notes                                          |
| ---------------- | ------------------- | ------------------------------- | --------------------- | ---------------------------------------------- |
| `.c`             | Source              | C source code                   | GCC, Clang, MSVC, ICC | Standard C source                              |
| `.C`             | Source              | C++ source                      | GCC, Unix             | Uppercase C historically indicates C++ on Unix |
| `.cc`            | Source              | C++ source                      | GCC, Clang            | Very common on Linux                           |
| `.cpp`           | Source              | C++ source                      | All                   | Most common C++ extension                      |
| `.cxx`           | Source              | C++ source                      | GCC, Clang            | Common in scientific projects                  |
| `.cp`            | Source              | C++ source                      | Legacy                | Rare today                                     |
| `.c++`           | Source              | C++ source                      | Legacy                | Historical extension                           |
| `.ii`            | Preprocessed Source | Preprocessed C++                | GCC, Clang            | Output of `-E` for C++                         |
| `.i`             | Preprocessed Source | Preprocessed C                  | GCC, Clang            | Output after preprocessing                     |
| `.mi`            | Preprocessed Source | Preprocessed Objective-C        | GCC                   | Rare                                           |
| `.mii`           | Preprocessed Source | Preprocessed Objective-C++      | GCC                   | Rare                                           |
| `.h`             | Header              | Shared declarations             | All                   | Standard header                                |
| `.hh`            | Header              | C++ header                      | GCC                   | Popular on Linux                               |
| `.hpp`           | Header              | C++ header                      | All                   | Most common C++ header                         |
| `.hxx`           | Header              | C++ header                      | GCC, Clang            | Common in libraries                            |
| `.hp`            | Header              | C++ header                      | Legacy                | Historical                                     |
| `.h++`           | Header              | C++ header                      | Legacy                | Historical                                     |
| `.inc`           | Include             | Shared include file             | Various               | Used outside C++ too                           |
| `.def`           | Definition          | Windows export definitions      | MSVC                  | DLL exports                                    |
| `.idl`           | Interface           | COM/RPC definitions             | MSVC                  | Interface Definition Language                  |
| `.odl`           | Interface           | Object Definition Language      | Windows               | Mostly obsolete                                |
| `.dlg`           | Resource            | Dialog description              | Windows               | Older Win32 projects                           |
| `.rh`            | Resource Header     | Resource identifiers            | Windows               | Included by `.rc`                              |
| `.rc`            | Resource            | Windows resources               | MSVC                  | Icons, dialogs, menus                          |
| `.rc2`           | Resource            | Non-editable resources          | MSVC                  | Often preserved by Visual Studio               |
| `.resx`          | Resource            | Managed resources               | Visual Studio         | Mixed-language projects                        |
| `.inl`           | Inline              | Inline function implementations | All                   | Frequently paired with headers                 |
| `.ipp`           | Template            | Template implementations        | Boost                 | Very common in Boost                           |
| `.tpp`           | Template            | Template definitions            | Various               | Popular naming convention                      |
| `.txx`           | Template            | Template implementations        | ITK, VTK              | Scientific libraries                           |
| `.tpl`           | Template            | Template implementation         | Various               | Less common                                    |
| `.impl`          | Implementation      | Inline/template implementation  | Various               | Rare                                           |
| `.inc.hpp`       | Include             | Generated include header        | Build systems         | Generated during builds                        |
| `.generated.h`   | Generated Header    | Auto-generated header           | Unreal Engine         | Reflection/macros                              |
| `.generated.cpp` | Generated Source    | Auto-generated source           | Unreal Engine         | Generated by Unreal Header Tool                |
| `.moc`           | Generated Source    | Meta-object code                | Qt                    | Generated by Qt MOC                            |
| `.ui`            | UI Definition       | Qt Designer form                | Qt                    | XML UI file                                    |
| `.qrc`           | Resource            | Qt resource collection          | Qt                    | Compiled into executable                       |
| `.pri`           | Project Include     | Qt project include              | qmake                 | Shared project settings                        |
| `.pro`           | Project             | Qt project file                 | qmake                 | Older Qt builds                                |
| `.ixx`           | Module              | C++20 module interface          | MSVC, Clang           | Common module extension                        |
| `.cppm`          | Module              | C++20 module interface          | Clang, GCC            | Most popular today                             |
| `.mpp`           | Module              | C++20 module interface          | MSVC                  | Microsoft examples                             |
| `.mxx`           | Module              | C++20 module interface          | Legacy                | Older proposal                                 |
| `.cxxm`          | Module              | Module source                   | Experimental          | Rare                                           |
| `.cppm.in`       | Module              | Generated module                | CMake                 | Template-generated                             |
| `.ixx.in`        | Module              | Generated module                | Build systems         | Configuration template                         |
| `.modulemap`     | Module Map          | Clang modules                   | Clang                 | Maps headers into modules                      |
| `.modmap`        | Module Map          | Clang modules                   | Clang                 | Alternative name                               |
| `.module`        | Module Metadata     | Module configuration            | Various               | Vendor-specific                                |
| `.pcm`           | Compiled Module     | Binary module                   | Clang/MSVC            | Produced after compilation                     |
| `.ifc`           | Compiled Module     | Interface file                  | MSVC                  | "Interface File Content"                       |
| `.cmi`           | Compiled Module     | Compiled module interface       | GCC                   | GCC modules                                    |
| `.gcm`           | Compiled Module     | GCC compiled module             | GCC                   | GCC implementation                             |
| `.bmi`           | Compiled Module     | Binary Module Interface         | Generic               | Vendor-independent term                        |
| `.hbm`           | Header Unit         | Header binary module            | Experimental          | Rare                                           |
| `.hif`           | Header Interface    | Header unit                     | Experimental          | Rare                                           |
| `.ixh`           | Header Unit         | Module header                   | Experimental          | Proposal                                       |
| `.m`             | Source              | Objective-C                     | Apple Clang           | Apple ecosystem                                |
| `.mm`            | Source              | Objective-C++                   | Apple Clang           | C++ with Objective-C                           |
| `.s`             | Assembly            | Assembly source                 | All                   | Output from compiler or handwritten            |
| `.S`             | Assembly            | Preprocessed assembly           | GCC, Clang            | Runs through preprocessor                      |
| `.sx`            | Assembly            | Preprocessed assembly           | GCC                   | Less common                                    |
| `.asm`           | Assembly            | Assembly source                 | MASM, NASM            | Widely used on Windows                         |
| `.asmx`          | Assembly            | Assembly-related source         | Proprietary           | Rare                                           |
| `.mac`           | Macro Assembly      | Macro assembly source           | Legacy assemblers     | Historical                                     |
| `.msa`           | Assembly            | Macro source                    | Embedded tools        | Vendor-specific                                |
| `.h.in`          | Template Header     | Configure-generated header      | Autotools             | Input for `configure`                          |
| `.hpp.in`        | Template Header     | Generated C++ header            | CMake                 | Processed during configuration                 |
| `.hh.in`         | Template Header     | Generated header                | Build systems         | Rare                                           |
| `.c.in`          | Template Source     | Generated C source              | Autotools             | Configuration input                            |
| `.cpp.in`        | Template Source     | Generated C++ source            | CMake                 | Processed before compilation                   |
| `.cc.in`         | Template Source     | Generated source                | Build systems         | Less common                                    |
| `.cxx.in`        | Template Source     | Generated source                | Build systems         | Less common                                    |
| `.h.in.cmake`    | Template            | CMake configured header         | CMake                 | Used with `configure_file()`                   |
| `.hpp.in.cmake`  | Template            | Configured C++ header           | CMake                 | Common in libraries                            |
| `.ixx.in.cmake`  | Template            | Configured module interface     | CMake                 | Emerging usage                                 |
| `.cppm.in.cmake` | Template            | Configured module interface     | CMake                 | Emerging usage                                 |
| `.pch`           | Precompiled Header  | Cached parsed header            | MSVC                  | Improves compile times                         |
| `.gch`           | Precompiled Header  | GCC precompiled header          | GCC                   | Generated from header                          |
| `.pchi`          | Precompiled Header  | Clang precompiled header        | Clang                 | LLVM format                                    |
| `.ast`           | Serialized AST      | Compiler AST snapshot           | Clang                 | Used for tooling and analysis    


# C/C++ File Extensions Reference — Part 2
### Compiler Intermediate Files (LLVM, GCC, Clang, MSVC, Intel, LTO & Optimization Artifacts)

This section covers files produced internally by compilers during preprocessing, optimization, code generation, link-time optimization (LTO), static analysis, and diagnostics. Most of these are generated automatically and are rarely edited by hand.

| Extension                | Generated By    | Compiler Stage           | Purpose                          | Notes                                       |
| ------------------------ | --------------- | ------------------------ | -------------------------------- | ------------------------------------------- |
| `.bc`                    | LLVM/Clang      | LLVM IR                  | LLVM Bitcode                     | Binary LLVM Intermediate Representation     |
| `.ll`                    | LLVM/Clang      | LLVM IR                  | LLVM IR                          | Human-readable LLVM IR                      |
| `.thinlto.bc`            | Clang           | ThinLTO                  | ThinLTO Bitcode                  | Distributed LTO input                       |
| `.lto.bc`                | Clang           | Full LTO                 | Link-Time Optimization bitcode   | Used for whole-program optimization         |
| `.opt.bc`                | LLVM            | Optimization             | Optimized bitcode                | Internal optimization output                |
| `.linked.bc`             | LLVM            | Linking                  | Linked LLVM IR                   | Combined bitcode modules                    |
| `.import.bc`             | LLVM            | ThinLTO                  | Imported IR                      | Cross-module optimization                   |
| `.internal.bc`           | LLVM            | Internal                 | Internal bitcode                 | Toolchain-generated                         |
| `.preopt.bc`             | LLVM            | Before Optimization      | Original bitcode                 | Before optimization passes                  |
| `.postopt.bc`            | LLVM            | After Optimization       | Optimized bitcode                | After optimization pipeline                 |
| `.remarks`               | LLVM            | Optimization             | Optimization remarks             | Human-readable report                       |
| `.opt.yaml`              | LLVM            | Optimization             | YAML optimization report         | Used with optimization remarks              |
| `.opt.json`              | LLVM            | Optimization             | JSON optimization report         | Machine-readable                            |
| `.opt-record.json`       | Clang           | Optimization             | Optimization record              | Generated with `-fsave-optimization-record` |
| `.yaml`                  | LLVM            | Analysis                 | Optimization metadata            | Generic YAML diagnostics                    |
| `.plist`                 | Clang           | Static Analysis          | Analyzer report                  | Used by Clang Static Analyzer               |
| `.sarif`                 | Clang           | Analysis                 | SARIF report                     | Static-analysis standard format             |
| `.dia`                   | Clang           | Diagnostics              | Serialized diagnostics           | Used by IDEs                                |
| `.diag`                  | Various         | Diagnostics              | Diagnostic log                   | Vendor-specific                             |
| `.ast`                   | Clang           | Parsing                  | Serialized Abstract Syntax Tree  | Used by libclang                            |
| `.pcm`                   | Clang           | Modules                  | Precompiled Module               | Binary module cache                         |
| `.pch`                   | Clang/MSVC      | Parsing                  | Precompiled Header               | Speeds compilation                          |
| `.gch`                   | GCC             | Parsing                  | Precompiled Header               | GCC version                                 |
| `.pchi`                  | Clang           | Parsing                  | Internal PCH                     | Clang-specific                              |
| `.ifc`                   | MSVC            | Modules                  | Interface file                   | C++20 Modules                               |
| `.cmi`                   | GCC             | Modules                  | Compiled Module Interface        | GCC Modules TS                              |
| `.gcm`                   | GCC             | Modules                  | GCC module                       | Binary module                               |
| `.bmi`                   | Various         | Modules                  | Binary Module Interface          | Generic term                                |
| `.ii`                    | GCC/Clang       | Preprocessing            | Preprocessed C++                 | Output of `-E`                              |
| `.i`                     | GCC/Clang       | Preprocessing            | Preprocessed C                   | Output of `-E`                              |
| `.mi`                    | GCC             | Preprocessing            | Objective-C                      | Rare                                        |
| `.mii`                   | GCC             | Preprocessing            | Objective-C++                    | Rare                                        |
| `.s`                     | Compiler        | Assembly                 | Generated assembly               | Unix assembly                               |
| `.S`                     | Compiler        | Assembly                 | Preprocessed assembly            | Runs through preprocessor                   |
| `.sx`                    | GCC             | Assembly                 | Extended assembly                | Rare                                        |
| `.asm`                   | Compiler        | Assembly                 | Assembly listing                 | Windows assemblers                          |
| `.cod`                   | MSVC            | Code Generation          | Assembly listing                 | Generated with `/FA`                        |
| `.lst`                   | Various         | Assembly                 | Listing file                     | Mixed source/assembly                       |
| `.lis`                   | Various         | Assembly                 | Listing file                     | Vendor-specific                             |
| `.map`                   | Linker          | Linking                  | Memory map                       | Symbol addresses                            |
| `.exp`                   | MSVC Linker     | Linking                  | Export table                     | DLL exports                                 |
| `.ilk`                   | MSVC            | Incremental Linking      | Incremental linker database      | Faster relinking                            |
| `.idb`                   | MSVC            | Compilation              | Incremental compiler DB          | Legacy incremental build info               |
| `.ipdb`                  | MSVC            | Optimization             | Program database                 | Incremental link optimization               |
| `.iobj`                  | MSVC            | Optimization             | Intermediate object              | Whole Program Optimization                  |
| `.obj`                   | Compiler        | Code Generation          | Object file                      | COFF format                                 |
| `.o`                     | Compiler        | Code Generation          | Object file                      | ELF/Mach-O object                           |
| `.lo`                    | Libtool         | Build                    | Libtool object                   | GNU Libtool                                 |
| `.su`                    | GCC             | Analysis                 | Stack usage report               | `-fstack-usage`                             |
| `.gcno`                  | GCC             | Coverage                 | Coverage notes                   | Compile-time coverage                       |
| `.gcda`                  | GCC             | Coverage                 | Coverage data                    | Runtime coverage                            |
| `.gcov`                  | GCC             | Coverage                 | Coverage report                  | Generated by gcov                           |
| `.profraw`               | LLVM            | Profiling                | Raw profile                      | LLVM profiler                               |
| `.profdata`              | LLVM            | Profiling                | Merged profile                   | Used by PGO                                 |
| `.proftext`              | LLVM            | Profiling                | Text profile                     | Less common                                 |
| `.fdata`                 | GCC             | Feedback                 | Profile-guided optimization      | AutoFDO                                     |
| `.afdo`                  | GCC             | Feedback                 | AutoFDO profile                  | Google AutoFDO                              |
| `.bolt`                  | LLVM BOLT       | Optimization             | Binary optimization data         | Post-link optimizer                         |
| `.bolt.yaml`             | LLVM BOLT       | Optimization             | BOLT metadata                    | YAML format                                 |
| `.dyn`                   | Optimizer       | Analysis                 | Dynamic profile                  | Vendor-specific                             |
| `.ipa`                   | GCC             | Interprocedural Analysis | IPA dump                         | Internal optimization                       |
| `.jump`                  | GCC             | Optimization             | Jump optimization dump           | Internal pass                               |
| `.sched`                 | GCC             | Scheduling               | Scheduler dump                   | Instruction scheduling                      |
| `.tree`                  | GCC             | GIMPLE                   | Tree dump                        | AST/GIMPLE dump                             |
| `.gimple`                | GCC             | GIMPLE                   | GIMPLE dump                      | Intermediate representation                 |
| `.cfg`                   | GCC             | CFG                      | Control Flow Graph               | Compiler dump                               |
| `.rtl`                   | GCC             | RTL                      | Register Transfer Language       | Internal IR                                 |
| `.ssa`                   | GCC             | SSA                      | Static Single Assignment         | Optimization form                           |
| `.vrp`                   | GCC             | Optimization             | Value Range Propagation          | Dump file                                   |
| `.alias`                 | GCC             | Optimization             | Alias analysis                   | Dump                                        |
| `.inline`                | GCC             | Optimization             | Inlining decisions               | Dump                                        |
| `.vect`                  | GCC             | Vectorization            | Vectorization report             | SIMD optimization                           |
| `.loop`                  | GCC             | Loop Optimization        | Loop optimization report         | Internal dump                               |
| `.combine`               | GCC             | RTL                      | Combine pass                     | Internal                                    |
| `.reload`                | GCC             | RTL                      | Register reload                  | Internal                                    |
| `.cse`                   | GCC             | Optimization             | Common subexpression elimination | Dump                                        |
| `.dom`                   | GCC             | Optimization             | Dominator optimization           | Dump                                        |
| `.fre`                   | GCC             | Optimization             | Full redundancy elimination      | Dump                                        |
| `.dce`                   | GCC             | Optimization             | Dead code elimination            | Dump                                        |
| `.eh`                    | GCC             | Exception Handling       | EH optimization                  | Internal                                    |
| `.reassoc`               | GCC             | Optimization             | Reassociation pass               | Dump                                        |
| `.tailc`                 | GCC             | Optimization             | Tail call optimization           | Dump                                        |
| `.unroll`                | GCC             | Optimization             | Loop unrolling                   | Dump                                        |
| `.vector`                | GCC             | Optimization             | Vectorizer output                | Dump                                        |
| `.ltrans`                | GCC             | LTO                      | Local transformation             | LTO partition                               |
| `.wpa`                   | GCC             | LTO                      | Whole Program Analysis           | LTO stage                                   |
| `.lto.o`                 | GCC             | LTO                      | LTO object                       | Contains IR                                 |
| `.lto.s`                 | GCC             | LTO                      | Assembly after LTO               | Internal                                    |
| `.thinlto`               | LLVM            | ThinLTO                  | ThinLTO cache                    | Internal metadata                           |
| `.cache`                 | LLVM            | LTO                      | Module cache                     | Cached compilation artifacts                |
| `.rsp`                   | Linker/Compiler | Build                    | Response file                    | Stores long command lines                   |
| `.cmd`                   | MSVC            | Build                    | Compiler command file            | Generated by build systems                  |
| `.tmp`                   | Any compiler    | Temporary                | Temporary compilation file       | Deleted after build                         |
| `.bak`                   | Various         | Backup                   | Backup artifact                  | Not compiler-specific                       |
| `.trace`                 | Compiler        | Diagnostics              | Compilation trace                | Performance/debugging                       |
| `.timing`                | Compiler        | Diagnostics              | Timing report                    | Compile-time performance                    |
| `.json`                  | Clang           | Diagnostics              | Compilation database             | Often `compile_commands.json`               |
| `.compile_commands.json` | CMake/Clang     | Tooling                  | Compilation database             | Used by clangd, clang-tidy                  |


# C/C++ File Extensions Reference — Part 3
### Object Files, Libraries, Executables, Debug Symbols, Linker Outputs, Profiling, Coverage & Runtime Artifacts

This part focuses on the artifacts produced after compilation: object files, libraries, executables, debugging information, linker outputs, profiling and coverage data, and runtime support files.

| Extension       | Artifact Type                   | Produced By      | Used By           | Platform / Toolchain | Description                          |
| --------------- | ------------------------------- | ---------------- | ----------------- | -------------------- | ------------------------------------ |
| `.o`            | Object File                     | Compiler         | Linker            | ELF, Mach-O          | Standard Unix object file            |
| `.obj`          | Object File                     | Compiler         | Linker            | COFF (Windows)       | Windows object file                  |
| `.lo`           | Object File                     | GNU Libtool      | Libtool           | Unix                 | Libtool object wrapper               |
| `.a`            | Static Library                  | Archiver (`ar`)  | Linker            | Unix/Linux           | Static archive library               |
| `.lib`          | Static Library / Import Library | Librarian        | Linker            | Windows              | Static library or DLL import library |
| `.lai`          | Libtool Metadata                | Libtool          | Libtool           | Unix                 | Internal Libtool info                |
| `.la`           | Libtool Archive                 | Libtool          | Libtool           | Unix                 | Metadata for shared/static libraries |
| `.so`           | Shared Library                  | Linker           | Dynamic Loader    | Linux                | Shared object                        |
| `.so.1`         | Versioned Library               | Linker           | Loader            | Linux                | SONAME version                       |
| `.so.2`         | Versioned Library               | Linker           | Loader            | Linux                | Alternate version                    |
| `.dll`          | Dynamic Library                 | Linker           | Windows Loader    | Windows              | Dynamic Link Library                 |
| `.dylib`        | Dynamic Library                 | Linker           | macOS Loader      | macOS                | Dynamic library                      |
| `.bundle`       | Loadable Module                 | Linker           | Runtime           | macOS                | Dynamically loaded bundle            |
| `.framework`    | Framework Bundle                | Xcode            | Runtime           | macOS/iOS            | Apple framework package              |
| `.xcframework`  | Multi-platform Framework        | Xcode            | Apple SDKs        | Apple                | Cross-platform framework bundle      |
| `.exe`          | Executable                      | Linker           | OS Loader         | Windows              | Windows executable                   |
| `.out`          | Executable                      | Linker           | OS Loader         | Unix                 | Default executable name              |
| `.elf`          | Executable                      | Linker           | OS Loader         | Linux                | ELF executable                       |
| `.bin`          | Raw Binary                      | Linker/Objcopy   | Hardware          | Embedded             | Raw machine code                     |
| `.hex`          | Intel HEX                       | Objcopy          | Bootloader        | Embedded             | Flash programming format             |
| `.srec`         | Motorola S-record               | Objcopy          | Bootloader        | Embedded             | Firmware image                       |
| `.mot`          | Motorola Record                 | Objcopy          | Bootloader        | Embedded             | Firmware format                      |
| `.uf2`          | UF2 Firmware                    | Toolchain        | Bootloader        | Embedded             | USB Flashing Format                  |
| `.rom`          | ROM Image                       | Linker           | Emulator          | Embedded             | ROM binary                           |
| `.img`          | Binary Image                    | Linker           | Emulator          | Various              | Disk or firmware image               |
| `.iso`          | Disk Image                      | Build Tools      | Virtual Machines  | Various              | Optical disk image                   |
| `.wasm`         | WebAssembly Binary              | Emscripten/Clang | Browser/Runtime   | Web                  | WebAssembly module                   |
| `.js`           | JavaScript Glue                 | Emscripten       | Browser           | Web                  | Loader for Wasm                      |
| `.html`         | Generated Launcher              | Emscripten       | Browser           | Web                  | Demo page                            |
| `.mem`          | Memory Initialization           | Toolchain        | FPGA/Simulator    | Embedded             | Memory image                         |
| `.map`          | Linker Map                      | Linker           | Developer         | All                  | Symbol and memory layout             |
| `.exp`          | Export Table                    | Linker           | Linker            | Windows              | Exported symbols                     |
| `.imp`          | Import Table                    | Linker           | Linker            | Some toolchains      | Import symbol info                   |
| `.ilk`          | Incremental Link DB             | Linker           | Linker            | MSVC                 | Incremental linking                  |
| `.idb`          | Build Database                  | Compiler         | MSVC              | Windows              | Incremental compilation DB           |
| `.ipdb`         | PDB Metadata                    | MSVC             | Linker            | Windows              | Intermediate debug DB                |
| `.iobj`         | Intermediate Object             | MSVC             | Linker            | Windows              | Whole-program optimization           |
| `.pdb`          | Debug Symbols                   | Linker           | Debugger          | Windows              | Program Database                     |
| `.dbg`          | Debug Symbols                   | Linker           | Debugger          | Linux                | Separate debug info                  |
| `.dSYM`         | Debug Bundle                    | dsymutil         | LLDB              | macOS                | Debug symbol bundle                  |
| `.sym`          | Symbol File                     | Linker           | Debugger          | Various              | Symbol information                   |
| `.nm`           | Symbol Dump                     | `nm`             | Developer         | Unix                 | Exported symbol list                 |
| `.gdb_index`    | Debug Index                     | GDB              | Debugger          | Linux                | Accelerates symbol lookup            |
| `.dwz`          | Compressed DWARF                | `dwz`            | Debugger          | Linux                | Reduced debug info                   |
| `.dwarf`        | Debug Format                    | Compiler         | Debugger          | Unix                 | DWARF debugging data                 |
| `.eh_frame`     | Exception Metadata              | Compiler         | Runtime           | ELF                  | Stack unwinding data                 |
| `.eh_frame_hdr` | EH Header                       | Linker           | Runtime           | ELF                  | Exception metadata header            |
| `.pdata`        | Exception Table                 | Linker           | Runtime           | Windows              | Structured exception handling        |
| `.xdata`        | Exception Data                  | Linker           | Runtime           | Windows              | Exception metadata                   |
| `.reloc`        | Relocation Data                 | Linker           | Loader            | Windows              | Relocation table                     |
| `.rdata`        | Read-only Data                  | Linker           | Runtime           | Windows              | Constants section                    |
| `.edata`        | Export Data                     | Linker           | Loader            | Windows              | Export directory                     |
| `.idata`        | Import Data                     | Linker           | Loader            | Windows              | Import directory                     |
| `.bss`          | Uninitialized Data              | Linker           | Runtime           | ELF                  | Zero-initialized memory              |
| `.data`         | Initialized Data                | Linker           | Runtime           | ELF                  | Writable global variables            |
| `.text`         | Code Section                    | Compiler         | CPU               | ELF/COFF             | Machine instructions                 |
| `.rodata`       | Read-only Section               | Compiler         | Runtime           | ELF                  | Constants and literals               |
| `.ctors`        | Constructor Table               | Linker           | Runtime           | GCC                  | Static constructors                  |
| `.dtors`        | Destructor Table                | Linker           | Runtime           | GCC                  | Static destructors                   |
| `.init`         | Initialization Section          | Linker           | Runtime           | ELF                  | Startup routines                     |
| `.fini`         | Finalization Section            | Linker           | Runtime           | ELF                  | Cleanup routines                     |
| `.gcno`         | Coverage Notes                  | GCC              | `gcov`            | GCC                  | Static coverage metadata             |
| `.gcda`         | Coverage Data                   | Runtime          | `gcov`            | GCC                  | Runtime execution counts             |
| `.gcov`         | Coverage Report                 | `gcov`           | Developer         | GCC                  | Human-readable coverage              |
| `.profraw`      | Raw Profile                     | LLVM             | `llvm-profdata`   | LLVM                 | Raw execution profile                |
| `.profdata`     | Merged Profile                  | LLVM             | Compiler          | LLVM                 | Profile-guided optimization input    |
| `.proftext`     | Text Profile                    | LLVM             | Developer         | LLVM                 | Text profile representation          |
| `.fdata`        | AutoFDO Data                    | GCC              | Compiler          | GCC                  | Sample-based optimization            |
| `.afdo`         | AutoFDO Profile                 | Google           | GCC               | GCC                  | Profile-guided optimization          |
| `.cov`          | Coverage Report                 | Tools            | Developer         | Various              | Generic coverage report              |
| `.lcov`         | Coverage Data                   | `lcov`           | `genhtml`         | Linux                | LCOV coverage format                 |
| `.info`         | Coverage Metadata               | `lcov`           | Tools             | Linux                | Coverage summary                     |
| `.xml`          | Coverage Report                 | Tools            | CI                | Various              | XML coverage output                  |
| `.json`         | Coverage/Profile                | Tools            | CI                | Various              | JSON report                          |
| `.trace`        | Runtime Trace                   | Profiler         | Developer         | Various              | Execution trace                      |
| `.perf`         | Performance Data                | Linux `perf`     | `perf`            | Linux                | Performance counters                 |
| `.perf.data`    | Perf Database                   | Linux `perf`     | `perf`            | Linux                | Recorded profiling session           |
| `.callgrind`    | Call Graph                      | Valgrind         | KCachegrind       | Linux                | Function call profile                |
| `.cachegrind`   | Cache Profile                   | Valgrind         | KCachegrind       | Linux                | Cache simulation results             |
| `.massif`       | Heap Profile                    | Valgrind         | Massif Visualizer | Linux                | Heap memory usage                    |
| `.helgrind`     | Thread Analysis                 | Valgrind         | Developer         | Linux                | Data race analysis                   |
| `.drd`          | Thread Checker                  | Valgrind         | Developer         | Linux                | Concurrency analysis                 |
| `.memcheck`     | Memory Report                   | Valgrind         | Developer         | Linux                | Memory error log                     |
| `.asan`         | AddressSanitizer Log            | ASan             | Developer         | LLVM/GCC             | AddressSanitizer output              |
| `.lsan`         | LeakSanitizer Log               | LSan             | Developer         | LLVM                 | Leak report                          |
| `.tsan`         | ThreadSanitizer Log             | TSan             | Developer         | LLVM                 | Thread race report                   |
| `.ubsan`        | UndefinedBehavior Log           | UBSan            | Developer         | LLVM/GCC             | Undefined behavior report            |
| `.san`          | Sanitizer Report                | Various          | Developer         | Various              | Generic sanitizer output             |
| `.core`         | Core Dump                       | OS               | Debugger          | Unix                 | Crash memory dump                    |
| `.dmp`          | Memory Dump                     | OS               | Debugger          | Windows              | Crash dump                           |
| `.mdmp`         | Minidump                        | Windows          | Debugger          | Windows              | Smaller crash dump                   |
| `.crash`        | Crash Report                    | Runtime          | Developer         | macOS/Linux          | Application crash log                |


# C/C++ File Extensions Reference — Part 4
### Build Systems, Package Managers, IDE Files, Resources, Documentation & Static Analysis

This part covers the ecosystem around C++ development rather than the compiler itself: build systems, dependency managers, IDE metadata, documentation generators, configuration files, resources, static analysis outputs, and project files.


| Extension                   | Category      | Tool / Ecosystem | Purpose                                   | Human Editable | Notes                           |
| --------------------------- | ------------- | ---------------- | ----------------------------------------- | -------------- | ------------------------------- |
| `.cmake`                    | Build         | CMake            | CMake script/module                       | ✅              | Functions, macros, find modules |
| `CMakeLists.txt`            | Build         | CMake            | Main build script                         | ✅              | Entry point for CMake           |
| `.cmake.in`                 | Build         | CMake            | Template configured by `configure_file()` | ✅              | Generates final files           |
| `.cmake-format.yaml`        | Build         | CMake            | Formatting configuration                  | ✅              | Used by `cmake-format`          |
| `.cmake-lint.yaml`          | Build         | CMake            | Lint configuration                        | ✅              | Style checks                    |
| `.ninja`                    | Build         | Ninja            | Build graph                               | ❌              | Generated by CMake/Meson        |
| `.ninja_deps`               | Build         | Ninja            | Dependency database                       | ❌              | Internal                        |
| `.ninja_log`                | Build         | Ninja            | Build log                                 | ❌              | Incremental builds              |
| `Makefile`                  | Build         | GNU Make         | Build instructions                        | ✅              | Standard Makefile               |
| `.mk`                       | Build         | Make             | Included Makefile                         | ✅              | Shared rules                    |
| `.mak`                      | Build         | NMake            | Windows Makefile                          | ✅              | MSVC                            |
| `.make`                     | Build         | Make             | Alternative Makefile                      | ✅              | Less common                     |
| `.gmk`                      | Build         | GNU Make         | GNU Make include                          | ✅              | Rare                            |
| `.am`                       | Build         | Automake         | Automake source                           | ✅              | Generates Makefile.in           |
| `.ac`                       | Build         | Autoconf         | Configuration script                      | ✅              | configure.ac                    |
| `.m4`                       | Build         | Autoconf         | Macro definitions                         | ✅              | Autoconf macros                 |
| `.in`                       | Build         | Autotools        | Input template                            | ✅              | Used by configure               |
| `.pc`                       | Package       | pkg-config       | Package description                       | ✅              | Compiler/linker flags           |
| `.pc.in`                    | Package       | pkg-config       | Template                                  | ✅              | Generated during configure      |
| `.meson`                    | Build         | Meson            | Build file (historical)                   | ✅              | Rare                            |
| `meson.build`               | Build         | Meson            | Main build file                           | ✅              | Standard Meson                  |
| `meson_options.txt`         | Build         | Meson            | User options                              | ✅              | Meson configuration             |
| `.bzl`                      | Build         | Bazel            | Build extension                           | ✅              | Starlark language               |
| `BUILD`                     | Build         | Bazel            | Build rules                               | ✅              | Bazel target file               |
| `BUILD.bazel`               | Build         | Bazel            | Explicit BUILD file                       | ✅              | Preferred by Bazel              |
| `WORKSPACE`                 | Build         | Bazel            | Workspace definition                      | ✅              | Legacy                          |
| `MODULE.bazel`              | Build         | Bazel            | Module dependencies                       | ✅              | Modern Bazel                    |
| `Jamfile`                   | Build         | Boost.Build      | Build description                         | ✅              | Boost.Build                     |
| `Jamroot`                   | Build         | Boost.Build      | Root build file                           | ✅              | Project root                    |
| `.jam`                      | Build         | Boost.Build      | Included Jam file                         | ✅              | Rules/macros                    |
| `build2`                    | Build         | build2           | Build manifest                            | ✅              | build2 ecosystem                |
| `.bp`                       | Build         | Android Soong    | Blueprint file                            | ✅              | Android builds                  |
| `.gn`                       | Build         | GN               | Build configuration                       | ✅              | Chromium                        |
| `.gni`                      | Build         | GN               | Included configuration                    | ✅              | Shared GN settings              |
| `.sln`                      | IDE           | Visual Studio    | Solution file                             | ✅              | Multiple projects               |
| `.vcxproj`                  | IDE           | Visual Studio    | C++ project                               | ✅              | MSBuild XML                     |
| `.vcproj`                   | IDE           | Visual Studio    | Legacy project                            | ✅              | Deprecated                      |
| `.vcxproj.filters`          | IDE           | Visual Studio    | Virtual folders                           | ✅              | IDE organization                |
| `.vcxproj.user`             | IDE           | Visual Studio    | User settings                             | ✅              | Local machine                   |
| `.props`                    | IDE           | MSBuild          | Shared properties                         | ✅              | Project settings                |
| `.targets`                  | IDE           | MSBuild          | Build targets                             | ✅              | MSBuild tasks                   |
| `.filters`                  | IDE           | Visual Studio    | File grouping                             | ✅              | Older projects                  |
| `.vsconfig`                 | IDE           | Visual Studio    | Required workloads                        | ✅              | Team setup                      |
| `.suo`                      | IDE           | Visual Studio    | User options                              | ❌              | Binary                          |
| `.opensdf`                  | IDE           | Visual Studio    | IntelliSense DB                           | ❌              | Legacy                          |
| `.sdf`                      | IDE           | Visual Studio    | IntelliSense DB                           | ❌              | Deprecated                      |
| `.VC.db`                    | IDE           | Visual Studio    | Browse database                           | ❌              | Modern replacement              |
| `.VC.opendb`                | IDE           | Visual Studio    | Open database                             | ❌              | Temporary                       |
| `.ipch`                     | IDE           | Visual Studio    | IntelliSense PCH                          | ❌              | Cached                          |
| `.code-workspace`           | IDE           | VS Code          | Multi-root workspace                      | ✅              | JSON                            |
| `.code-profile`             | IDE           | VS Code          | Profile                                   | ✅              | User settings                   |
| `.clangd`                   | Tooling       | clangd           | Language server config                    | ✅              | YAML                            |
| `.clang-format`             | Tooling       | Clang            | Formatting rules                          | ✅              | Very common                     |
| `.clang-tidy`               | Tooling       | Clang            | Static analysis config                    | ✅              | YAML                            |
| `.clang-query`              | Tooling       | Clang            | Query configuration                       | ✅              | AST matcher                     |
| `.editorconfig`             | Tooling       | EditorConfig     | Shared editor settings                    | ✅              | Cross-editor                    |
| `.ccls`                     | Tooling       | ccls             | Language server config                    | ✅              | Alternative to clangd           |
| `.compile_commands.json`    | Tooling       | CMake            | Compilation database                      | ❌              | Generated                       |
| `.bear`                     | Tooling       | Bear             | Capture build database                    | ❌              | Internal                        |
| `.cache`                    | Tooling       | Various          | Cache                                     | ❌              | Generic                         |
| `.json`                     | Config        | Various          | Configuration                             | ✅              | Universal                       |
| `.yaml`                     | Config        | Various          | Configuration                             | ✅              | Human-friendly                  |
| `.yml`                      | Config        | Various          | Configuration                             | ✅              | Alias of YAML                   |
| `.toml`                     | Config        | Various          | Configuration                             | ✅              | Conan 2, tools                  |
| `.xml`                      | Config        | Various          | Configuration                             | ✅              | Widely used                     |
| `.ini`                      | Config        | Various          | INI configuration                         | ✅              | Windows/common                  |
| `.cfg`                      | Config        | Various          | Generic configuration                     | ✅              | Common                          |
| `.conf`                     | Config        | Unix             | System configuration                      | ✅              | Linux                           |
| `.properties`               | Config        | Java/Gradle      | Properties                                | ✅              | Cross-language                  |
| `.env`                      | Config        | dotenv           | Environment variables                     | ✅              | Runtime configuration           |
| `.lock`                     | Package       | Various          | Dependency lock file                      | ❌              | Generated                       |
| `.conanfile.py`             | Package       | Conan 1          | Package recipe                            | ✅              | Python API                      |
| `.conanfile.txt`            | Package       | Conan            | Simple package recipe                     | ✅              | Legacy                          |
| `.conanfile`                | Package       | Conan            | Generic recipe                            | ✅              | Rare                            |
| `.vcpkg.json`               | Package       | vcpkg            | Manifest mode                             | ✅              | Modern vcpkg                    |
| `.vcpkg-configuration.json` | Package       | vcpkg            | Registry configuration                    | ✅              | Custom registries               |
| `.manifest`                 | Package       | Various          | Package manifest                          | ✅              | Generic                         |
| `.lock.json`                | Package       | Various          | Lock metadata                             | ❌              | Generated                       |
| `.dox`                      | Documentation | Doxygen          | Documentation source                      | ✅              | Standalone pages                |
| `.doxyfile`                 | Documentation | Doxygen          | Main configuration                        | ✅              | No extension                    |
| `.tag`                      | Documentation | Doxygen          | Cross-project tags                        | ❌              | Generated                       |
| `.qhp`                      | Documentation | Qt Help          | Help project                              | ✅              | Qt Assistant                    |
| `.qch`                      | Documentation | Qt Help          | Compiled help                             | ❌              | Generated                       |
| `.md`                       | Documentation | Markdown         | README/docs                               | ✅              | Most common                     |
| `.rst`                      | Documentation | reStructuredText | Sphinx docs                               | ✅              | Python & C++                    |
| `.txt`                      | Documentation | Generic          | Plain text                                | ✅              | Universal                       |
| `.html`                     | Documentation | Doxygen          | Generated docs                            | ❌              | Output                          |
| `.pdf`                      | Documentation | LaTeX            | Generated manual                          | ❌              | Output                          |
| `.svg`                      | Documentation | Vector graphics  | Diagrams                                  | ✅              | Documentation assets            |
| `.png`                      | Documentation | Images           | Screenshots                               | ✅              | Assets                          |
| `.jpg`                      | Documentation | Images           | Photos                                    | ✅              | Assets                          |
| `.dot`                      | Documentation | Graphviz         | Graph description                         | ✅              | UML/call graphs                 |
| `.dia`                      | Documentation | Dia              | Diagrams                                  | ✅              | Diagram source                  |
| `.plantuml`                 | Documentation | PlantUML         | UML diagrams                              | ✅              | Text-based UML                  |
| `.puml`                     | Documentation | PlantUML         | UML diagrams                              | ✅              | Short extension                 |
| `.sarif`                    | Analysis      | Static analyzers | Standard analysis report                  | ❌              | Security tools                  |
| `.plist`                    | Analysis      | Clang Analyzer   | Analysis results                          | ❌              | Apple/Clang                     |
| `.xml`                      | Analysis      | Various          | Analysis report                           | ❌              | Checkstyle/Cppcheck             |
| `.json`                     | Analysis      | Various          | Machine-readable report                   | ❌              | CI integration                  |
| `.csv`                      | Analysis      | Various          | Metrics export                            | ❌              | Reports                         |
| `.log`                      | Analysis      | Various          | Analysis log                              | ❌              | Generic logs                    |
| `.err`                      | Analysis      | Various          | Error output                              | ❌              | Build/analysis errors           |
| `.out`                      | Analysis      | Various          | Analysis output                           | ❌              | Generic output                  |
| `.cov`                      | Analysis      | Coverage tools   | Coverage summary                          | ❌              | Tool-dependent                  |
| `.report`                   | Analysis      | Various          | Generic report                            | ❌              | Vendor-specific                 |



# C/C++ File Extensions Reference — Part 5
### CUDA, HIP, SYCL, OpenCL, Embedded Systems, WebAssembly, Legacy, Vendor-Specific & Miscellaneous Files

This final part collects specialized and less common extensions used in GPU programming, heterogeneous computing, embedded development, firmware, cross-compilation, vendor toolchains, reverse engineering, and historical C/C++ ecosystems.

| Extension       | Ecosystem           | Category       | Purpose                                 | Status       | Notes                      |
| --------------- | ------------------- | -------------- | --------------------------------------- | ------------ | -------------------------- |
| `.cu`           | CUDA                | Source         | CUDA C++ source                         | Active       | Main NVIDIA CUDA source    |
| `.cuh`          | CUDA                | Header         | CUDA header                             | Active       | Device/host declarations   |
| `.fatbin`       | CUDA                | Binary         | Fat binary (multiple GPU architectures) | Active       | Embedded in executables    |
| `.cubin`        | CUDA                | Binary         | Compiled GPU binary                     | Active       | NVIDIA GPU machine code    |
| `.ptx`          | CUDA                | Intermediate   | Parallel Thread Execution assembly      | Active       | Virtual ISA                |
| `.sass`         | CUDA                | Assembly       | GPU assembly                            | Active       | Generated from PTX         |
| `.nvvm`         | CUDA                | IR             | NVIDIA LLVM IR                          | Active       | Internal compilation stage |
| `.nvinfo`       | CUDA                | Metadata       | CUDA metadata                           | Active       | GPU information            |
| `.gpu`          | CUDA                | Config         | GPU configuration                       | Rare         | Vendor-specific            |
| `.hip`          | HIP                 | Source         | HIP C++ source                          | Active       | AMD ROCm                   |
| `.hip.cpp`      | HIP                 | Source         | HIP implementation                      | Active       | Common naming              |
| `.hip.h`        | HIP                 | Header         | HIP header                              | Active       | Device declarations        |
| `.hsaco`        | HIP                 | Binary         | HSA Code Object                         | Active       | AMD GPU binary             |
| `.amdgcn`       | HIP                 | Binary         | AMD GCN binary                          | Active       | GPU ISA                    |
| `.spv`          | SYCL/OpenCL         | Binary         | SPIR-V intermediate                     | Active       | Khronos standard           |
| `.spir`         | OpenCL              | IR             | SPIR intermediate                       | Legacy       | Before SPIR-V              |
| `.spirv`        | OpenCL              | IR             | Alternative SPIR-V naming               | Active       | Rare extension             |
| `.sycl`         | SYCL                | Source         | SYCL source                             | Experimental | Mostly `.cpp` is used      |
| `.cl`           | OpenCL              | Source         | OpenCL kernel                           | Active       | Kernel language            |
| `.clcpp`        | OpenCL              | Source         | OpenCL C++ kernel                       | Rare         | C++ for OpenCL             |
| `.ocl`          | OpenCL              | Source         | OpenCL program                          | Legacy       | Vendor-specific            |
| `.metal`        | Apple Metal         | Source         | Metal shading language                  | Active       | Apple GPU programming      |
| `.air`          | Apple Metal         | IR             | Metal intermediate                      | Active       | Apple compiler output      |
| `.metallib`     | Apple Metal         | Binary         | Compiled Metal library                  | Active       | GPU runtime                |
| `.glsl`         | OpenGL              | Shader         | GLSL shader                             | Active       | Vertex/fragment shaders    |
| `.vert`         | OpenGL              | Shader         | Vertex shader                           | Active       | Graphics pipeline          |
| `.frag`         | OpenGL              | Shader         | Fragment shader                         | Active       | Pixel stage                |
| `.geom`         | OpenGL              | Shader         | Geometry shader                         | Active       | Geometry processing        |
| `.tesc`         | OpenGL              | Shader         | Tessellation control                    | Active       | Tessellation stage         |
| `.tese`         | OpenGL              | Shader         | Tessellation evaluation                 | Active       | Tessellation stage         |
| `.comp`         | OpenGL              | Shader         | Compute shader                          | Active       | GPU compute                |
| `.hlsl`         | DirectX             | Shader         | High-Level Shader Language              | Active       | Microsoft DirectX          |
| `.fx`           | DirectX             | Shader         | Effect file                             | Legacy       | Older DirectX              |
| `.fxh`          | DirectX             | Header         | Effect include                          | Legacy       | Included by `.fx`          |
| `.ispc`         | ISPC                | Source         | Intel SPMD Program Compiler             | Active       | SIMD kernels               |
| `.gen`          | CodeGen             | Generated      | Auto-generated source                   | Active       | Generic suffix             |
| `.autogen.cpp`  | CodeGen             | Generated      | Generated implementation                | Active       | Qt, protobuf, etc.         |
| `.autogen.h`    | CodeGen             | Generated      | Generated header                        | Active       | Build systems              |
| `.pb.cc`        | Protobuf            | Source         | Generated C++ source                    | Active       | Protocol Buffers           |
| `.pb.h`         | Protobuf            | Header         | Generated header                        | Active       | Protocol Buffers           |
| `.grpc.pb.cc`   | gRPC                | Source         | Generated RPC source                    | Active       | gRPC                       |
| `.grpc.pb.h`    | gRPC                | Header         | Generated RPC header                    | Active       | gRPC                       |
| `.capnp.c++`    | Cap'n Proto         | Source         | Generated C++                           | Active       | Serialization              |
| `.capnp.h`      | Cap'n Proto         | Header         | Generated header                        | Active       | Serialization              |
| `.thrift`       | Apache Thrift       | IDL            | Interface definition                    | Active       | RPC framework              |
| `.proto`        | Protocol Buffers    | IDL            | Message definitions                     | Active       | Generates C++              |
| `.fbs`          | FlatBuffers         | IDL            | Schema definition                       | Active       | Serialization              |
| `.idl`          | CORBA/COM           | IDL            | Interface definition                    | Active       | Generates C++              |
| `.odl`          | COM                 | IDL            | Object Definition Language              | Legacy       | Older COM                  |
| `.asn`          | ASN.1               | Schema         | Data schema                             | Active       | Telecom/security           |
| `.asn1`         | ASN.1               | Schema         | Alternative extension                   | Active       | Standards                  |
| `.ld`           | GNU Linker          | Linker         | Linker script                           | Active       | Memory layout              |
| `.lds`          | GNU Linker          | Linker         | Linker script                           | Active       | Embedded systems           |
| `.icf`          | IAR                 | Linker         | Linker configuration                    | Active       | IAR Embedded Workbench     |
| `.scf`          | Keil                | Linker         | Scatter-loading file                    | Active       | ARM/Keil                   |
| `.map`          | Linker              | Report         | Memory map                              | Active       | Embedded & desktop         |
| `.elf`          | Embedded            | Executable     | ELF image                               | Active       | Firmware                   |
| `.axf`          | ARM                 | Executable     | ARM Executable                          | Active       | Keil MDK                   |
| `.abs`          | Embedded            | Executable     | Absolute binary                         | Active       | Various toolchains         |
| `.out`          | TI DSP              | Executable     | TI executable                           | Active       | TI Code Composer           |
| `.coff`         | Embedded            | Object         | COFF executable                         | Legacy       | Older toolchains           |
| `.omf`          | Object              | Binary         | Object Module Format                    | Legacy       | DOS/Windows                |
| `.rel`          | Embedded            | Object         | Relocatable object                      | Active       | 8-bit compilers            |
| `.ihx`          | SDCC                | Firmware       | Intel HEX output                        | Active       | Small Device C Compiler    |
| `.eep`          | AVR                 | EEPROM         | EEPROM image                            | Active       | AVR microcontrollers       |
| `.lss`          | AVR                 | Listing        | Mixed source/disassembly                | Active       | avr-objdump                |
| `.sym`          | Embedded            | Symbols        | Symbol table                            | Active       | Debugging                  |
| `.lst`          | Embedded            | Listing        | Assembly listing                        | Active       | Mixed output               |
| `.dis`          | Reverse Engineering | Disassembly    | Decompiled assembly                     | Active       | objdump/IDA                |
| `.asm`          | Assembly            | Source         | Assembly source                         | Active       | Handwritten/generated      |
| `.sig`          | Signature           | Metadata       | Binary signature                        | Active       | Vendor-specific            |
| `.pat`          | IDA Pro             | Signature      | Pattern signature                       | Active       | Reverse engineering        |
| `.til`          | IDA Pro             | Type Library   | Type information                        | Active       | Reverse engineering        |
| `.idb`          | IDA Pro             | Database       | Analysis database                       | Legacy       | Old IDA                    |
| `.i64`          | IDA Pro             | Database       | 64-bit database                         | Active       | Current IDA                |
| `.ghidra`       | Ghidra              | Project        | Reverse engineering                     | Active       | NSA Ghidra                 |
| `.bndb`         | Binary Ninja        | Database       | Analysis database                       | Active       | Binary Ninja               |
| `.r2`           | radare2             | Project        | Analysis session                        | Active       | radare2                    |
| `.cache`        | Generic             | Cache          | Cached data                             | Active       | Various tools              |
| `.bak`          | Generic             | Backup         | Backup copy                             | Active       | Editor/tool output         |
| `.orig`         | Generic             | Backup         | Original file                           | Active       | Patch utilities            |
| `.rej`          | Patch               | Rejected patch | Active                                  | `patch` tool |                            |
| `.diff`         | Version Control     | Patch          | Differences                             | Active       | Unified diff               |
| `.patch`        | Version Control     | Patch          | Source patch                            | Active       | Git, GNU patch             |
| `.manifest`     | Deployment          | Manifest       | Application metadata                    | Active       | Windows, package managers  |
| `.appxmanifest` | Windows             | Manifest       | UWP application                         | Active       | Windows Store              |
| `.rc`           | Windows             | Resource       | Resources                               | Active       | Icons, dialogs             |
| `.res`          | Windows             | Resource       | Compiled resources                      | Active       | Linked into binaries       |
| `.cab`          | Windows             | Archive        | Cabinet package                         | Active       | Installers                 |
| `.msi`          | Windows             | Installer      | Windows Installer                       | Active       | Software deployment        |
| `.deb`          | Linux               | Package        | Debian package                          | Active       | Distribution package       |
| `.rpm`          | Linux               | Package        | RPM package                             | Active       | Red Hat ecosystem          |
| `.pkg`          | macOS               | Installer      | macOS package                           | Active       | Apple installer            |
| `.AppImage`     | Linux               | Package        | Portable application                    | Active       | Linux distribution         |
| `.snap`         | Linux               | Package        | Snap package                            | Active       | Canonical                  |
| `.flatpak`      | Linux               | Package        | Flatpak bundle                          | Active       | Desktop Linux              |
| `.xz`           | Compression         | Archive        | Compressed package                      | Active       | Source releases            |
| `.bz2`          | Compression         | Archive        | Compressed package                      | Active       | Source releases            |
| `.gz`           | Compression         | Archive        | Compressed package                      | Active       | Source releases            |
| `.zip`          | Compression         | Archive        | ZIP archive                             | Active       | Universal                  |
| `.7z`           | Compression         | Archive        | 7-Zip archive                           | Active       | High compression           |
| `.tar`          | Compression         | Archive        | Tape archive                            | Active       | Unix packaging             |
| `.tgz`          | Compression         | Archive        | tar.gz shorthand                        | Active       | Source packages            |


C/C++ Ecosystem File Extensions - SUMMARY


|  # | Category                | Typical Stage         | Approx. Count | Common Extensions                                                       | Generated By / Used By |
| -: | ----------------------- | --------------------- | ------------: | ----------------------------------------------------------------------- | ---------------------- |
|  1 | Source Files            | Development           |            12 | `.c`, `.cc`, `.cpp`, `.cxx`, `.cp`, `.c++`, `.C`                        | Programmer             |
|  2 | Header Files            | Development           |            15 | `.h`, `.hpp`, `.hh`, `.hxx`, `.hp`, `.h++`                              | Programmer             |
|  3 | Template & Inline Files | Development           |            12 | `.ipp`, `.tpp`, `.txx`, `.tpl`, `.inl`, `.impl`                         | Programmer             |
|  4 | Generated Sources       | Build                 |            12 | `.generated.cpp`, `.generated.h`, `.pb.cc`, `.grpc.pb.cc`, `.moc`       | Code generators        |
|  5 | Resource Files          | Build                 |            10 | `.rc`, `.res`, `.qrc`, `.ui`, `.rh`, `.rc2`                             | Resource compiler      |
|  6 | C++20 Modules           | Compilation           |            18 | `.cppm`, `.ixx`, `.mpp`, `.mxx`, `.pcm`, `.ifc`, `.cmi`, `.gcm`, `.bmi` | Compiler               |
|  7 | Preprocessed Files      | Preprocessing         |             6 | `.i`, `.ii`, `.mi`, `.mii`                                              | Preprocessor           |
|  8 | Assembly Files          | Code Generation       |             8 | `.s`, `.S`, `.sx`, `.asm`, `.cod`, `.lst`                               | Compiler               |
|  9 | LLVM IR                 | Optimization          |            15 | `.bc`, `.ll`, `.thinlto.bc`, `.opt.bc`                                  | Clang/LLVM             |
| 10 | GCC IR                  | Optimization          |            20 | `.gimple`, `.rtl`, `.ssa`, `.tree`, `.cfg`                              | GCC                    |
| 11 | LTO / ThinLTO           | Optimization          |            10 | `.lto.o`, `.ltrans`, `.wpa`, `.thinlto`                                 | GCC/LLVM               |
| 12 | Object Files            | Compilation           |             5 | `.o`, `.obj`, `.lo`                                                     | Compiler               |
| 13 | Static Libraries        | Linking               |             5 | `.a`, `.lib`, `.la`, `.lai`                                             | Archiver               |
| 14 | Shared Libraries        | Linking               |             8 | `.so`, `.dll`, `.dylib`, `.bundle`, `.framework`                        | Linker                 |
| 15 | Executables             | Linking               |            12 | `.exe`, `.elf`, `.out`, `.bin`, `.hex`, `.wasm`                         | Linker                 |
| 16 | Firmware Images         | Embedded              |             8 | `.uf2`, `.hex`, `.rom`, `.img`, `.srec`, `.eep`                         | Embedded toolchains    |
| 17 | Linker Files            | Linking               |            10 | `.map`, `.exp`, `.imp`, `.ilk`, `.ld`, `.lds`                           | Linker                 |
| 18 | Debug Symbols           | Debugging             |            15 | `.pdb`, `.dbg`, `.dSYM`, `.sym`, `.dwarf`                               | Compiler/Linker        |
| 19 | Coverage Files          | Testing               |            10 | `.gcda`, `.gcno`, `.gcov`, `.lcov`                                      | GCC/LLVM               |
| 20 | Profiling Files         | Optimization          |            12 | `.profraw`, `.profdata`, `.perf.data`, `.callgrind`                     | Profilers              |
| 21 | Sanitizer Reports       | Debugging             |             8 | `.asan`, `.tsan`, `.ubsan`, `.lsan`                                     | Sanitizers             |
| 22 | Crash Dumps             | Debugging             |             5 | `.core`, `.dmp`, `.mdmp`, `.crash`                                      | Operating System       |
| 23 | Compiler Diagnostics    | Analysis              |            12 | `.dia`, `.plist`, `.remarks`, `.opt.yaml`                               | Compiler               |
| 24 | Build Systems           | Build                 |            30 | `.cmake`, `.mk`, `.mak`, `.ninja`, `.bzl`, `BUILD`                      | Build systems          |
| 25 | IDE Files               | Development           |            18 | `.sln`, `.vcxproj`, `.code-workspace`, `.VC.db`                         | IDE                    |
| 26 | Configuration Files     | Configuration         |            15 | `.json`, `.yaml`, `.toml`, `.cfg`, `.ini`                               | Tools                  |
| 27 | Package Managers        | Dependency Management |            12 | `.pc`, `.vcpkg.json`, `.conanfile.py`                                   | Package managers       |
| 28 | Documentation           | Documentation         |            15 | `.md`, `.rst`, `.dox`, `.pdf`, `.svg`                                   | Documentation tools    |
| 29 | Static Analysis         | Analysis              |            10 | `.sarif`, `.xml`, `.csv`, `.report`                                     | Static analyzers       |
| 30 | CUDA Files              | GPU Computing         |            10 | `.cu`, `.cuh`, `.ptx`, `.fatbin`, `.cubin`                              | NVIDIA CUDA            |
| 31 | HIP Files               | GPU Computing         |             5 | `.hip`, `.hsaco`, `.amdgcn`                                             | AMD ROCm               |
| 32 | OpenCL / SYCL           | GPU Computing         |             8 | `.cl`, `.spir`, `.spv`, `.sycl`                                         | Khronos                |
| 33 | Graphics Shaders        | Graphics              |            10 | `.vert`, `.frag`, `.comp`, `.geom`, `.metal`                            | Graphics APIs          |
| 34 | Serialization / RPC     | Code Generation       |            10 | `.proto`, `.thrift`, `.fbs`, `.capnp.h`                                 | Generators             |
| 35 | Embedded Linker Files   | Embedded              |             8 | `.icf`, `.scf`, `.ld`, `.lds`                                           | Embedded toolchains    |
| 36 | Reverse Engineering     | Security              |            12 | `.i64`, `.bndb`, `.ghidra`, `.pat`                                      | RE tools               |
| 37 | Patch & Version Control | Development           |             6 | `.diff`, `.patch`, `.rej`, `.orig`                                      | Git/Patch              |
| 38 | Installers              | Deployment            |             8 | `.msi`, `.deb`, `.rpm`, `.pkg`, `.AppImage`                             | Packaging tools        |
| 39 | Archives                | Distribution          |             8 | `.zip`, `.tar`, `.7z`, `.xz`, `.gz`                                     | Archivers              |
| 40 | Miscellaneous           | Various               |           20+ | `.cache`, `.bak`, `.manifest`, `.tmp`                                   | Various                |


## C++ Build Pipeline
Source Files
    │
    ▼
Headers / Modules
    │
    ▼
Preprocessor
(.i .ii)
    │
    ▼
Compiler Frontend
(AST)
    │
    ▼
LLVM IR / GCC GIMPLE
(.ll .bc .gimple .rtl)
    │
    ▼
Optimizer
(LTO / ThinLTO)
    │
    ▼
Assembly
(.s .asm)
    │
    ▼
Object Files
(.o .obj)
    │
    ▼
Libraries
(.a .lib .so .dll .dylib)
    │
    ▼
Linker
    │
    ▼
Executable
(.exe .elf .out .wasm)
    │
    ├─────────────► Debug
    │                 (.pdb .dSYM .dbg)
    │
    ├─────────────► Coverage
    │                 (.gcda .gcno)
    │
    ├─────────────► Profiling
    │                 (.profraw .perf.data)
    │
    └─────────────► Crash Dumps
                      (.core .dmp)


## Toolchain → Common File Types
| Tool              | Most Common Extensions                                                             |
| ----------------- | ---------------------------------------------------------------------------------- |
| **GCC**           | `.cpp`, `.hpp`, `.ii`, `.o`, `.a`, `.so`, `.gcda`, `.gimple`, `.rtl`, `.ssa`       |
| **Clang/LLVM**    | `.cpp`, `.ll`, `.bc`, `.pcm`, `.profraw`, `.profdata`, `.plist`                    |
| **MSVC**          | `.cpp`, `.vcxproj`, `.obj`, `.lib`, `.dll`, `.exe`, `.pdb`, `.ilk`, `.idb`, `.ifc` |
| **Intel oneAPI**  | `.cpp`, `.o`, `.obj`, `.bc`, `.profraw`                                            |
| **CUDA (NVCC)**   | `.cu`, `.cuh`, `.ptx`, `.cubin`, `.fatbin`                                         |
| **HIP (ROCm)**    | `.hip`, `.hsaco`, `.amdgcn`                                                        |
| **Emscripten**    | `.wasm`, `.js`, `.html`                                                            |
| **Qt**            | `.pro`, `.pri`, `.ui`, `.qrc`, `.moc`                                              |
| **CMake**         | `CMakeLists.txt`, `.cmake`, `compile_commands.json`                                |
| **Visual Studio** | `.sln`, `.vcxproj`, `.props`, `.targets`                                           |
| **Bazel**         | `BUILD`, `MODULE.bazel`, `.bzl`                                                    |
| **Meson**         | `meson.build`, `meson_options.txt`                                                 |


## Grand Totals
| Section                         | Approximate Entries |
| ------------------------------- | ------------------: |
| Source & Language Files         |                 ~70 |
| Compiler Intermediate Files     |                 ~95 |
| Binary & Runtime Files          |                 ~90 |
| Build & Development Files       |                 ~95 |
| Specialized, GPU & Legacy Files |                ~100 |
| **Total Covered**               | **~450 extensions** |

