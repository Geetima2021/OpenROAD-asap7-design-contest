
# OpenROAD 7nm design contest

This repository gives an insight of my experience in the OpenROAD ASAP7 (7nm) physical design contest organise by VSD and OpenROAD which was held from 15 March 2023 to 31st March 2023. In this contest I have used both cloud as well as my local system in exploring available design ibex and other a RISCV based design rvmyth which is built duing the RISCV Myth workshop organised by VSD and its details is available [here](https://github.com/shivanishah269/risc-v-core). 

Prior moving ahead towards the contest problem, let me take you along to my installation journey, give you a picture of the issues I encountered and the actions taken to resolve the issues.

My system configuration
1. 4 cpu core and 4GB Ram
2. Ubuntu 18.04

The Openroad tool can be build locally or with a docker. I have build the tool locally. The steps involve in building the tool locally and the issues faced will be discussed as and when encountered . For latest build locally, visit [here](https://openroad-flow-scripts.readthedocs.io/en/latest/user/BuildLocally.html) and using docker [click](https://openroad-flow-scripts.readthedocs.io/en/latest/user/BuildWithDocker.html). 

Build locally 

1. git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
2. cd /home/geetima/OpenROAD-flow-scripts/tools/OpenROAD
3. sudo ./etc/DependencyInstaller.sh

During this stage I have encountered few issues
   a. 
   
     ![libtcl_issue](Images/Error/libtcl_issue,png)




The problem statement initially decided is to reduce the runtime of the ibex design based on the given system configuration.

<!--![sys_info1](https://user-images.githubusercontent.com/63381455/229187714-43f9e318-238a-492f-81ff-61a3a8eec805.png)

![sys_info2](https://user-images.githubusercontent.com/63381455/229187725-62c34ef5-0911-470e-8271-ee89da58d3b7.png)--->

While executing the run for ibex design with the above system configuation detail routing has timing issues as the 0th optimization had taken around 11hrs with 4Gb ram and 6Gb swap area. The aim is to reduce the time taken for the exectuion of ibex design and the other aim is to start the execution from the point the routing [stopped](https://github.com/Geetima2021/OpenROAD-flow-scripts/tree/GeetORFS/docs/contest).

The first thing done is to increase the swap area to 10GB and the available disk space is around 35GB and it has shown much improvement during the detail routing stage and the 0th iteration completed in 04:36:31 time and the 1st iteration till 60% has taken around 10hrs. Later checkpoint is included in the detail_route script and the respective asap7 config files as an additional arguments as shown in the snapshot. The checkpoint is a step forward to work on starting the detail routing stage at the point it stopped which may occur due to shut down of the system. The next step of the work is yet to be completed.


![checkpoint](https://user-images.githubusercontent.com/63381455/229198528-1b5ac5b2-e961-47a1-87be-dfe5d7727d6e.png)


# DESIGN: rvmyth 

Executed in cloud and the system information is included in the snapshot below.

![system_info_cloud](https://user-images.githubusercontent.com/63381455/229164863-33c10d10-1374-46ff-9cc9-09407635d784.png)


![ram_cloud](https://user-images.githubusercontent.com/63381455/229164479-713fb6ce-8679-4bc1-a3be-b07d8a5f006a.png)

The configuration file and the final result obtained is included in the snapshot below

![design_config](https://user-images.githubusercontent.com/63381455/229182847-f79f5900-4989-4534-b156-fce7a5aaaa1a.png)


![result](https://user-images.githubusercontent.com/63381455/229182859-74d1681b-93dd-4c2e-b318-938c7277d960.png)

The clock network and the final routed image is as shown in the figure

![clk_final_route](https://user-images.githubusercontent.com/63381455/229184329-123e98d0-8241-4874-b723-b4fdc1f363ce.png)

# Conclusion

Here the constraint use is the clock period constraint only and other constraints is to be included.

# Acknowledgement
- [Shivani Shah](https://github.com/shivanishah269),Teaching Assistant, VSD Corp. Pvt. Ltd.
- [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
- [Phillip Guhring](https://github.com/thesourcerer8), Software architect at Libresilicon Association.
- [Sumanta Kar](https://github.com/Eyantra698Sumanto), Senior Project Technical Assistant, IIT Bombay)
- [Vijayan Krishnan](https://github.com/vijayank88), Senior Application Engineer for OpenROAD Project
 




