# RVYNQ-v1
## Single Cycle RISC-V/32I CPU


## RTL Files Structure
##
|Directory|Definition|
|---------|----------|
| **/ALU**| This directory consist of 8 logical operations(SLL, AND, OR, SLT, SLTU, SRA, SRL, XOR) and 2 arithmatic operations(ADD and SUB). These VHDL files united in ALU file. ALU_cobtrol vhdl file is liable to operate ALU by genarating opsel signal according to ALU_opcodes coming from controller.|
|**Decoder**| Decoder VHDL module separates the 32 bit input instruction into 6 different output signals. These signals are connected to the several components such as register_file, controller, sign_extend etc.|
|**Controller**| This module generates control signals for overall architecture. There are 7 branches for 7 type of instructions. One of them is the custom instruction which is barret reduction. Important point on this controller branch is sig_stall signal. This signal stall the RISCV architecture during barret reduction process. It is important that stalling prevents the concatanation errors during execution of barret reduction.|
|**/Multiplexers**| There are 3 multiplexer companents named as "xxxx_xxxx_mux.vhd". These companents organizes inputs and outputs of the general structure. Such as input of ALU is register type or immediate type.|
|**/Barret_Modules**| All the modules needed for barret reduction is used in "barret_top.vhd". This component uses 4 vhdl modules called "priority, dict, mult, div". These modules used as in pseudocode in the report. There is a FSM inside the barret_top. Computation steps executed with order of (MemCheck(in case of hit Precomputation step is skipped) -> Precomputation -> Reduction -> Result)|
|**/Memory Files**| 256 bytes little endian memory implemented as a data memory. Store word and load word operations use this memory space. Instruct_mem file is used for operating the architecture there are branches for each instruction. These instructions are given manually as the output of the asm2mc algorithm which is given as top file of this project  |

## License

MIT
