# Composite Enclaves

This repo contains the code release for the paper: Composite Enclaves: Towards Disaggregated Trusted Execution. For the corresponding hardware platform check the [FPGA Platform](#fpga-platform).

Big thanks to the following open-source projects which make this project possible:

- [Keystone Enclave](https://github.com/keystone-enclave) (commit: 8175c673745e94eeb35da860bc5c7fe7c60adca0)
- [Ariane/CVA6](https://github.com/openhwgroup/cva6/) (commit: 5536dfe0180080d12074edd2d0b705738239a146)

## Notes

It will be hard to build and try the current version of the git patches within this repository. This is mainly because we had to adapt some of the software (e.g., the bootloader) to work with our hardware platform. Surprisingly, this breaks support for qemu. The upstream keystone repo has since progressed significantly (e.g., use OpenSBI as the bootloader) and it should now be easier to integrate everything into the new version. However, this has not been done nor tested yet. If there is enough interest, we will try to incooperate our changes into a more up-to-date keystone.

## FPGA Platform

We use a GenesysII FPGA board from digilent. To run the examples in this repo which do not include any peripherals, a CVA6 image with PMPs enables should suffice. CVA6 supports PMPs starting from commit 5536dfe0180080d12074edd2d0b705738239a146. Any later version with PMPs enabled should work. To test more usecases, we added some peripheral interfaces to PMOD headers on the board. These were either connected to an SPI, UART, or GPIO peripheral on the FPGA (xilinx IP). We do not release these changes due to licencing problems.

## TODO

- Instructions on how to apply the patches. The fiel `keystone.patch` includes all changes in the submodules aswell. However, keystone has a weird way to checkout the eyrie runtime. Therefore the patch for eyrie is separate.
- Explain how to build an image for CVA6. Requires some manual steps pieced together from the CVA6-sdk and keystone buildflow.
