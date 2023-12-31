
![image](https://github.com/Pavan2280/pes_asic_class/assets/131603225/dd691578-5cba-417c-949e-0270fca2539a)


# ASIC Flow Course 

This Repository Guides you to complete the ASIC flow from scratch 

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
  
## ASIC Flow Course Assignments - Guided by Kunal Ghosh
# Table of contents

<details>
<summary>DAY-1 : Introduction to RISC-V ISA and GNU compiler toolchain</summary>
<br>
  
+ Task-1 : C Program To Compute Sum From 1 to N (using gcc) & Spike Simulation And Debug (using RISCV)
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

+ Task-2 : To debug the ALP generated by the compiler
    ```
    spike -d pk 1_n_sun.o
    ```
    ![de](https://github.com/Pavan2280/pes_asic_class/assets/131603225/ac22b9e7-6c71-423a-bfd7-a445ec226e95)

+ Task-3 : Contents of main using different optimizer
   - Using 1 : -O1 optimizer
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -o1 mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    riscv64-unknown-elf-objdump -d 1_n_sum.o | less
    ```
    ![o1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/2765fb0e-439d-404d-8b39-ef2089ca746b)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    riscv64-unknown-elf-objdump -d 1_n_sum.o | less
    ```
   -  Using 2 : -Ofast optimizer
    ![ofast](https://github.com/Pavan2280/pes_asic_class/assets/131603225/cac8e8f0-1def-482b-9cbe-348f6ed8dc33)

+ Task-4 : Lab For Signed And Unsigned Numbers
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
</details>

<details>
<summary>DAY-2 : Introduction to ABI and basic verification flow</summary>
<br>
  
+ Task-1 : Sum 1 to N Using ASM and simulating C program with function call
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o 1_9custom.o 1_9custom.c load.s
    spike pk 1_9custom.o
    riscv64-unknown-elf-objdump -d 1_9custom.o | less
    ```  
    ![#8](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f1400495-8618-470f-9b3a-aa7c61b8eb6e)
    ![#8_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8311e3f6-fa0e-4eb7-84c1-7ef8488f6ea3)
    ![8_4_new](https://github.com/Pavan2280/pes_asic_class/assets/131603225/e88722d5-63b8-41e2-9e41-35c9bbf87080)

+  Task-2 : Lab To Run C-Program On RISC-V CPU
    ```
    chmod 777 rv32im.sh
    ./rv32im.sh
    ```
    ![#8_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/519d8386-d509-40d6-bfca-b1817b4d2bd9)
</details>

# RTL design using Verilog with SKY130 Technology

<details>
<summary>DAY-3 : Introduction to Verilog RTL design and Synthesis</summary>
<br>

+ Verilog RTL Design: RTL design is a method used in digital circuit design where the behavior of a system is described using a hardware description language (HDL) like Verilog. It focuses on describing how data is transferred and manipulated between registers, representing the functional blocks of a digital system. This abstraction level is closer to the actual hardware implementation, making it suitable for describing complex digital systems.

+ Behavioral vs. RTL: Verilog offers different levels of abstraction for design. Behavioral describes the system's functionality without specifying the details of how it is implemented, while RTL focuses on how data moves between registers and the logic that operates on that data. RTL design provides a higher level of detail and control over the hardware structure.

+ Registers and Combinational Logic: In RTL design, a digital system is composed of registers (flip-flops) that store data and combinational logic that processes the data. The data flow between registers is described using signals and assignments. Combinational logic is described using procedural blocks, where you specify how inputs are transformed into outputs using Verilog statements.

+ Synthesis: Once the RTL description is complete, the design can be synthesized. Synthesis is the process of transforming the RTL description into a gate-level netlist, which represents the design using actual logic gates and flip-flops. This netlist can then be used to create physical layouts for fabrication. Synthesis tools optimize the design for factors like area, power, and timing.

+ Design Hierarchy: Larger systems are often broken down into hierarchical modules, each with its own RTL description. These modules communicate with each other using defined interfaces. This modular approach makes it easier to manage complexity and allows for reusable designs. Hierarchical designs can be synthesized together to create a complete system.

# Introduction to open-source simulator iverilog

+ Iverilog Based Simulation Flow

![iv](https://github.com/Pavan2280/pes_asic_class/assets/131603225/da9c25d9-c1dd-4f47-8e2e-edd5a839e3c8)

+ Task-1 :  Implementation of Mux using iverilog
    + Command to execute code
    ```
    gvim tb_good_mux.v -o good_mux.v
    iverilog good_mux.v tb_good_mux.v
    ./a.out
    gtkwave tb_good_mux.vcd
    ```
    ![3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/1c9c3e3e-4094-458f-8aff-a946cf9bd002)
    
    ![2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f3b9ec50-9622-4bd5-b606-6cf2ac4d55d4)


+ Introduction to Yosys and Logic Synthesis

![y](https://github.com/Pavan2280/pes_asic_class/assets/131603225/96f84104-686e-4497-8c35-352a29b36268)


+ To Verify Synthesis
![y2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/5a3c649c-50c6-4795-8175-866ecd2e82a8)

+ Invoking the yosys
![4](https://github.com/Pavan2280/pes_asic_class/assets/131603225/3abb8715-30d4-4a6c-b974-a158b21902b5)

+ Task-2 : Yosys Implementation of good mux 
     + Command to execute code
    ```
    yosys
    read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    read_verilog good_mux.v
    synth -top good_mux
    abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    show
    ```
    ![6](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4a06298e-a4df-4620-b22d-4ef4ce4f97ff)
    ![8](https://github.com/Pavan2280/pes_asic_class/assets/131603225/aac0a282-d9fd-4d0d-8dee-cb96e3d99580)

+ Task-3 : Writing Netlist
     + Command to execute code
    ```
    write_verilog good_mux_netlist.v
    !gvim good_mux_netlist.v
    ``` 
    ![9](https://github.com/Pavan2280/pes_asic_class/assets/131603225/fcdb305a-9d2e-4268-a0b1-24e806fe01b8)
    
     + Command using switch
    ```
    write_verilog -noattr good_mux_netlist.v
    !gvim good_mux_netlist.v
    ``` 
    ![10](https://github.com/Pavan2280/pes_asic_class/assets/131603225/80ab17d9-5333-4c46-a69a-e504ae4a24db)
</details>

<details>
<summary>DAY-4 : Lab for Timing libs, hierarchical vs flat synthesis and efficient flop coding styles</summary>
<br>

![11](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d486468c-bc16-4719-bf35-1678423fc655)
![zz](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4fbe5e80-4116-4ea2-8109-f5cab90b04a9)

+ Task-1 : Hierarchial v/s flat synthesis
     + Command to execute code
    ```
    gvim multiple_modules.v
    yosys
    read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    read_verilog multiple_modules.v
    synth -top multiple_modules
    abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    show multiple_modules
    ```
    ![12](https://github.com/Pavan2280/pes_asic_class/assets/131603225/baee8db8-6d07-44ac-9852-6176cd718873)
    ![13](https://github.com/Pavan2280/pes_asic_class/assets/131603225/e0893369-9b03-4268-afcd-7635c005dbf4)
    ![14_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/0304633a-8014-4091-b3d1-66e70fc894d8)
    ![14_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/5707be74-79a7-4fba-9502-1d362e997ff2)
    ![15](https://github.com/Pavan2280/pes_asic_class/assets/131603225/abc77481-97ca-4ed7-88fe-b2242c450f4a)


     + Command to execute code
     ```
     write_verilog multiple_modules_hier.v
     !gvim multiple_modules_hier.v
     write_verilog -noattr multiple_modules_hier.v
     !gvim multiple_modules_hier.v
     flatten
     write_verilog -noattr multiple_modules_flat.v
     !gvim multiple_modules_flat.v
     ```
     ![16](https://github.com/Pavan2280/pes_asic_class/assets/131603225/766d8a5d-cdf4-45d8-848d-92850597f1cc)
     ![17](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d82d448a-866a-40e4-8779-52d65eab47e6)
     ![18](https://github.com/Pavan2280/pes_asic_class/assets/131603225/731046e6-f73c-4447-9866-b7966cbe48e5)
     ![19](https://github.com/Pavan2280/pes_asic_class/assets/131603225/2a271d1a-5607-425e-933c-856012fd8177)

+ Task-2 : Yosys Implementation
     + Command to execute code
     ```
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog multiple_modules.v
     synth -top multiple_modules
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     flatten
     show
     ```
     ![20](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8e7d0d08-11fc-4509-a121-213f0ac5d04b)

     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog multiple_modules.v
     synth -top sub_module1
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![21](https://github.com/Pavan2280/pes_asic_class/assets/131603225/de5cb545-5366-4676-a964-50481926748f)
     ![22](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a768fbc7-47e2-410c-a256-23091a0b6119)
     ![23](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d6c51ede-7c82-4566-9687-c6604ea0dc6c)

</details>

<details>
<summary>DAY-5:  Various flop coding styles , Combinational Logic & Sequential Logic Optimization</summary>
<br>

+ Task-1 : Iverilog Implementation
     + Command to execute code
     ``` 
     iverilog dff_asyncres.v tb_dff_asyncres.v
     ./a.out
     gtkwave tb_dff_asyncres.vcd
     ```
     ![26](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f5939de5-6d72-4229-b775-7505baa8a503)

     ```
     iverilog dff_async_set.v tb_dff_async_set.v
     ./a.out
     gtkwave tb_dff_async_set.vcd
     ```
     ![27](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4e9e5f32-a1cc-45b2-a02d-04781d794f59)

     ```
     iverilog dff_syncres.v tb_dff_syncres.v
     ./a.out
     gtkwave tb_dff_syncres.vcd
     ```
     ![28](https://github.com/Pavan2280/pes_asic_class/assets/131603225/65c85fc8-54b4-4cbf-a702-468415615e1c)

+ Task-2 : Yosys Implementation
     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog dff_asyncres.v
     synth -top dff_asyncres
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![29](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8cc2514d-bb8d-4bdb-911a-a26c25b97821)
     ![30](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8ced24ae-b96a-40c4-82fe-3540d3a49935)
     ![31](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d1e4bd8e-81c4-4790-bc4e-c98328150e4d)

     + Command to execute code
     ``` 
     read_verilog dff_async_set.v
     synth -top dff_async_set
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![32](https://github.com/Pavan2280/pes_asic_class/assets/131603225/e1d02d3d-b60c-441d-bada-01110ce1709a)

     + Command to execute code
     ``` 
     read_verilog dff_syncres.v
     synth -top dff_syncres
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![33](https://github.com/Pavan2280/pes_asic_class/assets/131603225/38b3950e-2e2e-4df0-928a-87ddb2b46b8b)

+ Task-3 : Mul2 & Mul8 Interesting optimisation
     + Command to execute code
     ```  
     gvim mult_*.v -o
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog mult_2.v
     synth -top mul2
     write_verilog -noattr mul2_net.v
     !gvim mul2_net.v
     ```
     ![34](https://github.com/Pavan2280/pes_asic_class/assets/131603225/69d154d4-26cf-483b-b200-fae950135a97)
     ![35](https://github.com/Pavan2280/pes_asic_class/assets/131603225/c12c597e-eb1c-4b62-8201-5b7aa68823de)
     ![36](https://github.com/Pavan2280/pes_asic_class/assets/131603225/fa4e247c-3f7f-47f7-9e6a-43655b1c6ad5)
     
     + Command to execute code
     ```  
     read_verilog mult_8.v
     synth -top mult8
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.li
     show
     write_verilog -noattr mult8_net.v
     !gvim mult8_net.v
     ```
     ![37](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4465ce93-496b-4718-b9c2-0940446ade9d)
     ![38](https://github.com/Pavan2280/pes_asic_class/assets/131603225/fc229382-7c57-4b37-bc87-804028eea844)

+ Task-4 : Yosys Implementation
     + Command to execute code
     ```
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog opt_check.v
     synth -top opt_check
     opt_clean -purge
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![41](https://github.com/Pavan2280/pes_asic_class/assets/131603225/0e339630-c1c5-42a0-9a29-9857a175760c)

     + Command to execute code
     ``` 
     read_verilog opt_check2.v
     synth -top opt_check2
     opt_clean -purge
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ``` 
     ![42](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f1363e7e-2666-4b6e-ba54-154f0954019e)


     + Command to execute code
     ```
     read_verilog opt_check3.v
     synth -top opt_check3
     opt_clean -purge
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![43](https://github.com/Pavan2280/pes_asic_class/assets/131603225/66e9918f-ee1b-49a9-8934-af88841a874a)

     + Command to execute code
     ``` 
     read_verilog opt_check4.v
     synth -top opt_check4
     opt_clean -purge
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![44](https://github.com/Pavan2280/pes_asic_class/assets/131603225/709e1228-e779-48d1-b3fb-05addeb6eecc)
  
     + Command to execute code
     ``` 
     read_verilog multiple_module_opt.v
     synth -top multiple_module_opt
     flatten
     opt_clean -purge                                                                                                                   
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ```
     ![45](https://github.com/Pavan2280/pes_asic_class/assets/131603225/929fc629-3bfb-4973-9643-83c7a0b679d7)

     + Command to execute code
     ``` 
     read_verilog multiple_module_opt.v
     synth -top multiple_module_opt
     flatten
     write_verilog -noattr
     multiple_module_opt_flat.v
     !gvim multiple_module_opt_flat.v
     ``` 
     ![46](https://github.com/Pavan2280/pes_asic_class/assets/131603225/85bed560-d616-4d57-81a5-44a8af0d592c)

     + Command to execute code
     ``` 
     read_verilog multiple_module_opt2.v
     synth -top multiple_module_opt2
     flatten
     opt_clean -purge                                                                                                                   
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     show
     ``` 
     ![47](https://github.com/Pavan2280/pes_asic_class/assets/131603225/61c06c2a-2e6e-4b7f-83e9-7fbb5359597d)

     + Command to execute code
     ``` 
     read_verilog multiple_module_opt2.v
     synth -top multiple_module_opt2
     flatten
     write_verilog -noattr
     multiple_module_opt2_flat.v
     !gvim multiple_module_opt2_flat.v
     ``` 
     ![48](https://github.com/Pavan2280/pes_asic_class/assets/131603225/74b9af1b-37b8-4258-ae3d-b9928417ac47)


+ Task-1 : Iverilog Implementation
     + Command to execute code
     ``` 
     iverilog dff_const1.v tb_dff_const1.v
     ./a.out   
     gtkwave tb_dff_const1.vcd
     ``` 
     ![50](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4b18f6b2-dc0a-441d-8fd6-437edfa8b1f0)

     + Command to execute code
     ``` 
     iverilog dff_const2.v tb_dff_const2.v
     ./a.out   
     gtkwave tb_dff_const2.vcd
     ```
     ![51](https://github.com/Pavan2280/pes_asic_class/assets/131603225/eb6d3a83-62f4-4015-a899-8ef47637c7fe)

     + Command to execute code
     ``` 
     iverilog dff_const3.v tb_dff_const3.v
     ./a.out   
     gtkwave tb_dff_const3.vcd
     ``` 
     ![55](https://github.com/Pavan2280/pes_asic_class/assets/131603225/390e4079-056d-491e-935b-b8019050345e)

     + Command to execute code
     ``` 
     iverilog dff_const4.v tb_dff_const4.v
     ./a.out   
     gtkwave tb_dff_const4.vcd
     ``` 
     ![57](https://github.com/Pavan2280/pes_asic_class/assets/131603225/32bdd966-0c5f-4a75-b4f0-6a2de94ec65c)

     + Command to execute code
     ``` 
     iverilog dff_const5.v tb_dff_const5.v
     ./a.out   
     gtkwave tb_dff_const4.vcd
     ```
     ![59](https://github.com/Pavan2280/pes_asic_class/assets/131603225/eeebdc43-57b2-4f3d-a6e6-811604fd4eb8)

+ Task-2 : Yosys Implementation
     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog dff_const1.v
     synth -top dff_const1
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![52](https://github.com/Pavan2280/pes_asic_class/assets/131603225/88a3ae20-dccb-4bb4-9c09-0a91ac3b9774)

     + Command to execute code
     ``` 
     read_verilog dff_const2.v
     synth -top dff_const2
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![53](https://github.com/Pavan2280/pes_asic_class/assets/131603225/0a86d30a-e031-416f-bfbc-090b26e127e7)

     + Command to execute code
     ``` 
     read_verilog dff_const3.v
     synth -top dff_const3
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![56](https://github.com/Pavan2280/pes_asic_class/assets/131603225/628994eb-683e-4f79-8cb5-46b6ab65e0cd)

     + Command to execute code
     ``` 
     read_verilog dff_const4.v
     synth -top dff_const4
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![58](https://github.com/Pavan2280/pes_asic_class/assets/131603225/985e9af4-ee44-4d8e-91ed-22e53dfd578d)

     + Command to execute code
     ``` 
     read_verilog dff_const5.v
     synth -top dff_const5
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ```
     ![60](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4b419170-65e9-438c-819c-c85eb0ad47f1)


+ Task-1 : Yosys Implementation
     + Command to execute code
     ``` 
     gvim counter_opt.v
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog counter_opt.v
     synth -top counter_opt
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![61](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4039b1ba-dd36-495d-a9be-3c3fde60c024)
     ![62](https://github.com/Pavan2280/pes_asic_class/assets/131603225/236ab3d3-f431-4505-934d-6bb8bd8eb33e)


     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog counter_opt2.v
     synth -top counter_opt
     dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     ``` 
     ![63](https://github.com/Pavan2280/pes_asic_class/assets/131603225/64dc68fc-199b-4211-aeb4-2b5178d43918)

</details>

<details>
<summary>DAY-6 : Labs on GLS and Synthesis-Simulation Mismatch</summary>
<br>
  
+ Task-1 : Iverilog Implementation
     + Command to execute code
     ``` 
     iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
     ./a.out
     gtkwave tb_ternary_operator_mux.vcd
     ``` 
     ![65](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d9557cc2-1f34-4042-a5b2-c6a8712eaffd)

     + Command to execute code
     ``` 
     iverilog bad_mux.v  tb_bad_mux.v
     ./a.out
     gtkwave tb_bad_mux.vcd
     ``` 
     ![68](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4c74bed7-e59f-4fc9-aa25-4714279ae544)

     + Command to execute code
     ``` 
     iverilog blocking_caveat.v tb_blocking_caveat.v
     ./a.out
     gtkwave tb_blocking_caveat.vcd
     ``` 
     ![71](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a603942d-af4c-4e56-9337-91ea52f60b6b)

+ Task-2 : Yosys & GLS Implementation
     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog ternary_operator_mux.v  
     synth -top ternary_operator_mux
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     write_verilog -noattr ternary_operator_mux_net.v
     show
     ``` 
     ![66](https://github.com/Pavan2280/pes_asic_class/assets/131603225/4057e980-6564-4d30-a28b-87f983950e48)

     + Command to execute code
     ``` 
     yosys
     read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     read_verilog blocking_caveat.v  
     synth -top blocking_caveat
     abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
     write_verilog -noattr blocking_caveat_net.v
     show
     ``` 
     ![72](https://github.com/Pavan2280/pes_asic_class/assets/131603225/60a06f7d-1f15-4a1d-b414-c58892a6a905)

     + Command to execute code
    ``` 
    iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
    ./a.out
    gtkwave tb_ternary_operator_mux.vcd 
    ``` 
    ![67](https://github.com/Pavan2280/pes_asic_class/assets/131603225/23c62dba-34fe-4421-b3ca-e0686a1ddfc5)

    + Command to execute code
    ``` 
    iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
    ./a.out
    gtkwave tb_bad_mux.vcd 
    ``` 
    ![69](https://github.com/Pavan2280/pes_asic_class/assets/131603225/066863c9-335b-4e3e-a932-e7d29b34ae53)

    + Command to execute code
    ``` 
    iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
    ./a.out
    gtkwave tb_blocking_caveat.vcd 
    ``` 
    ![73](https://github.com/Pavan2280/pes_asic_class/assets/131603225/0fe7f363-22f4-49eb-a717-45c80c1066c0)
</details>
