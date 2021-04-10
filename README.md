# ESP32_dissassembly_with_Arduino_IDE
.elf and .o to be disassembly, asm and listing will be produced


this is simple batch file, under windows.  
tested with Arduino IDE 1.8.13  

save this batch file to the project root of arduino compiling folder, you can see this folder with IDE and verbose info, for example, 
C:\Users\user0\AppData\Local\Temp\arduino_build_xxxx

structure like this usually,  

-- root\ *.elf, this bat file  
   --- skecch \ *.o  

output,  
-- root\ %project_name%_elf_dump.txt, %project_name%.asm  

```

set objdump="C:\Users\user0\AppData\Local\Arduino15\packages\esp32\tools\xtensa-esp32-elf-gcc\1.22.0-97-gc752ad5-5.2.0\bin\xtensa-esp32-elf-objdump.exe"

set project_name=project_1

set elf="%project_name%.ino.elf"
set o="./sketch/%project_name%.ino.cpp.o"

REM .elf to disasembly
%objdump% -C -d %elf% >> %project_name%_elf_dump.txt

REM .o to asm
%objdump% -d -M xtensa -S %o% >> %project_name%.asm

pause

```
