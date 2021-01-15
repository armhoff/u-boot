This path is a copy of the original
  https://github.com/cubieboard/u-boot-nand.git/branch/Cubietruck/nand_sunxi,
Note: except for the Makefile, this is identical to https://github.com/linux-sunxi/u-boot-sunxi.git

It has been modified as follows to work with mainline uBoot.

Migration steps:
  - initially copied from git/u-boot-nand/nand_sunxi:
    - lib
    - Makefile
  - additionally copied include files from git/u-boot-nand/arch/arm/include/asm/arch-sunxi/:
    - nand_bsp.h
       -> removed declarations of non existing methods:
          -> those might be used from nand_cmd:
            int sunxi_nand_read_opts(nand_info_t *nand, loff_t offset, size_t *length, u_char *buffer, int flags);
            int sunxi_nand_write_opts(nand_info_t *nand, loff_t offset, size_t *length, u_char *buffer, int flags);
            int sunxi_nand_erase_opts(nand_info_t *meminfo, const nand_erase_options_t *opts);
          -> never used:
            int sunxi_nand_flush_opts(nand_info_t *meminfo);
#endif
          
    - partition.h
       -> renamed this to partition_411.h
       -> copied partition.h from lichee/a10 branch -> partition_311.h
       -> partition.h minimized to include
          either partition_311.h or partition_411.h based on CONFIG_MACH_SUNxI
     
- EOF -
