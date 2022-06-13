add_executable(main
         main.c
         GC9A01.c
         image.c
         battery.c
         MPU9250.c
         phymodel.c
         prophet.c
         font24eng.c
         font24cyr.c
         prophet_ua.c
         prophet_en.c)


target_include_directories(main PRIVATE ../../pico-extras/src/rp2_common/pico_sleep/include ../../pico-sdk/src/rp2_common/hardware_rtc/include 
)


 # Import pico_stdlib which imports commonly used features
 target_link_libraries(main 
   pico_stdlib 
   hardware_spi 
   hardware_dma 
   hardware_adc 
   hardware_i2c 
   hardware_pwm 
   pico_multicore 
   hardware_sleep
        )

 # Create map/bin/hex file etc.
 pico_add_extra_outputs(main)

 # Add path via pico_set_program_url CMAKE
 example_auto_set_url(main)
 
 
pico_enable_stdio_usb(main 0) 
pico_enable_stdio_uart(main 1)