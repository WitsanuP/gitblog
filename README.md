# gitblog

about work dir

02_hardware/
    00_rtl/
    01_tb/
    02_filelist/
    03_script/
    04_sim/          # The simulation workspace
        work/        # Active tool run directory (ModelSim/VCS temporary compile files)
        log/         # Simulation stdout logs, lint reports, and error files (.log, .rpt)
        wave/        # Waveform database files (.vcd, .fsdb, .wcfg)

00_simulate (The Math/Algorithm)
01_fix_point_sim (The Quantization)
02_hdl (The Source Code & Verification)
03_synthesis / 03_fpga_impl (The Physical Implementation)
