# ASIC Flow Course
# Objective 
> VLSI ASIC design involves creating custom circuits optimized for specific tasks using RTL (Register-Transfer Level) description. This involves designing digital logic using hardware description languages like VHDL or Verilog, converting it to gate-level representation through synthesis, and eventually translating it into a physical layout for fabrication. The process includes architectural design, logic implementation, verification, and testing, resulting in highly efficient and tailored integrated circuits.

# Outcomes
+ RTL Description
+ Logic Synthesis
+ Physical Design
+ Verification

# Minimum Requirements for installation 
- ubuntu 20 + 
- min. disk space 150 Gb 
- RAM at least 6 Gb

# Steps for installation
- Enter these commands in terminal 
```
git clone https://github.com/kunalg123/riscv_workshop_collaterals
cd riscv_workshop_collaterals
chmod 755 run.sh
./run.sh 
```
  
# ASIC Flow Course Assignments - Guided by Kunal Ghosh
# Table of contents
+ DAY-1 : Introduction to RISC-V ISA and GNU compiler toolchain

   - Task-1 : C Program To Compute Sum From 1 to N (using gcc) & Spike Simulation And Debug (using RISCV)
    + Command to execute code using gcc
    ```
    gcc 1_n_sum.c
    ./a.out
    ```
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -o1 mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    spike pk 1_n_sun.o
    ```
    ![#4](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8b4e47d3-f3ba-40e1-b26d-166ee93ce174) 

   - Task-2 : To debug the ALP generated by the compiler
    ```
    spike -d pk 1_n_sun.o
    ```
    ![#4_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/9a9d88ea-acab-44fb-8af0-1ec5658b3cd8)

   - Task-3 : Lab For Signed And Unsigned Numbers
    + Command to execute code using gcc
    ```
    gcc us_highest.c
    ./a.out
    ```
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o us_highest.o us_highest.c
    spike pk us_highest.o
    ```
    ![#5](https://github.com/Pavan2280/pes_asic_class/assets/131603225/2f5ccf76-3dd3-4261-ad80-03ccf886ba55)
    ![#5_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a281e314-5894-4844-b281-528586984667)
    ![#5_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/693f403f-eee9-4a21-a46c-ee0e50dc461e)
    ![#5_3_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/b3e05a8e-8305-427d-9e3d-86add6fffdd9)
    ![#5_3_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/64d22154-52e0-492a-97e7-39287bf0dc0c)
    ![#5_3_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/73b13dab-457d-4739-9e3f-386a9f6ead6f)
    ![#5_4_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/eb62c0b2-f47d-4aef-8858-207a69387a3d)
    ![#5_4_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8c8ae69b-1158-4b69-8d57-fc97a51afc7f)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o s_highest.o s_highest.c
    spike pk s_highest.o
    ```
    ![#6_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d3f46dd8-f962-47c8-8603-f5bcf391e827)
    ![#6_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/ffd2fced-a464-45e8-be37-451147b8420a)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o signed_highest.o signed_highest.c
    spike pk signed_highest.o
    ```
    ![#7_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a1994ddc-1b9c-4497-8984-8b1dcddc66ff)
    ![#7_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d0ee8cd2-162a-4f00-b285-2b95f48bce44)

+ DAY-2 : Introduction to ABI and basic verification flow

   - Task-1 : Sum 1 to N Using ASM
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o 1_9custom.o 1_9custom.c load.s
    spike pk 1_9custom.o
    ```  
    ![#8](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f1400495-8618-470f-9b3a-aa7c61b8eb6e)
    ![#8_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8311e3f6-fa0e-4eb7-84c1-7ef8488f6ea3)

   -  Task-2 : Lab To Run C-Program On RISC-V CPU
    ```
    chmod 777 rv32im.sh
    ./rv32im.sh
    ```
    ![#8_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/519d8386-d509-40d6-bfca-b1817b4d2bd9)
