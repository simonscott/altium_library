*******************************************************************************
** © Copyright 2009 and 2010 Xilinx, Inc. All rights reserved.
** This file contains confidential and proprietary information of Xilinx, Inc. and 
** is protected under U.S. and international copyright and other intellectual property laws.
*******************************************************************************
**   ____  ____ 
**  /   /\/   / 
** /___/  \  /   Vendor: Xilinx 
** \   \   \/    
**  \   \        readme.txt Version: 1.1  
**  /   /        Date Last Modified:  03/18/10
** /___/   /\    Date Created: 07/29/09
** \   \  /  \   Associated Filenames: spartan6_ibis.zip, spartan6.ibs
**  \___\/\___\ 
** 
**  Device: Spartan-6 family
**  Revision History: 
**	1.1	First published Spartan-6 IBIS model file.
**      1.2     Internal build
**      1.3     Several additional standards added, several standards updated - see Revision History below
**   
*******************************************************************************
**
**  Disclaimer: 
**
**		This disclaimer is not a license and does not grant any rights to the materials 
**              distributed herewith. Except as otherwise provided in a valid license issued to you 
**              by Xilinx, and to the maximum extent permitted by applicable law: 
**              (1) THESE MATERIALS ARE MADE AVAILABLE "AS IS" AND WITH ALL FAULTS, 
**              AND XILINX HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS, EXPRESS, IMPLIED, OR STATUTORY, 
**              INCLUDING BUT NOT LIMITED TO WARRANTIES OF MERCHANTABILITY, NON-INFRINGEMENT, OR 
**              FITNESS FOR ANY PARTICULAR PURPOSE; and (2) Xilinx shall not be liable (whether in contract 
**              or tort, including negligence, or under any other theory of liability) for any loss or damage 
**              of any kind or nature related to, arising under or in connection with these materials, 
**              including for any direct, or any indirect, special, incidental, or consequential loss 
**              or damage (including loss of data, profits, goodwill, or any type of loss or damage suffered 
**              as a result of any action brought by a third party) even if such damage or loss was 
**              reasonably foreseeable or Xilinx had been advised of the possibility of the same.


**  Critical Applications:
**
**		Xilinx products are not designed or intended to be fail-safe, or for use in any application 
**		requiring fail-safe performance, such as life-support or safety devices or systems, 
**		Class III medical devices, nuclear facilities, applications related to the deployment of airbags,
**		or any other applications that could lead to death, personal injury, or severe property or 
**		environmental damage (individually and collectively, "Critical Applications"). Customer assumes 
**		the sole risk and liability of any use of Xilinx products in Critical Applications, subject only 
**		to applicable laws and regulations governing limitations on product liability.

**  THIS COPYRIGHT NOTICE AND DISCLAIMER MUST BE RETAINED AS PART OF THIS FILE AT ALL TIMES.

*******************************************************************************
** IMPORTANT NOTES **


1. This IBIS file is a work-in-progress, and does not yet contain models for the entire selection of Spartan-6 I/O standards.  If you have a request for a specific model that is not contained in this file, please contact Xilinx Technical Support: http://support.xilinx.com/support/clearexpress/websupport.htm


2. Model name nomenclature
				
[(io standard, and Vcco-level for all except HSTL)_(first letter of slew rate, or driver class)_("18" for HSTL Vcco=1.8V)_(drive_strength in mA)_(input or output termination)_(bank position)_(Vccaux level)]


# Notations used
					
Vcco and Vccaux Levels: 12 = 1.2V
			15 = 1.5V
			18 = 1.8V
			25 = 2.5V
			33 = 3.3V

Drive strength levels: 	2  = 2mA
			4  = 4mA
			6  = 6mA
			8  = 8mA
			12 = 12mA
			16 = 16mA
			24 = 24mA
F - Fast Slew rate	
Q - QuietIO slew rate
S - Slow Slew rate
I - Class-I output driver (SSTL and HSTL)
II - Class-II output driver (SSTL and HSTL)
III - Class-III output driver (SSTL and HSTL)
IN25 - Input termination is set to IN_TERM=UNTUNED_SPLIT_25
IN50 - Input termination is set to IN_TERM=UNTUNED_SPLIT_50
IN75 - Input termination is set to IN_TERM=UNTUNED_SPLIT_75
IN50M - special tuned Input termination only available for MCB designs, tuned for 50 Ohms
OT25 - Output termination is set to OUT_TERM=UNTUNED_25
OT50 - Output termination is set to OUT_TERM=UNTUNED_50
OT75 - Output termination is set to OUT_TERM=UNTUNED_75
TB - TOP/BOTTOM banks (banks 0 and 2)					
LR - LEFT/RIGHT banks (banks 1,3,4, and 5)			
LVCMJED - LVCMOS JEDEC
MDDR - MOBILE_DDR


# Nomenclature for the Differential Termination resistor

The Model for the optional Differential Termination resistor that can be assigned to differential input pins, uses the nomenclature:
	[rterm(Vcco level)_100_(Vccaux level)]
This Model can not be directly selected by the simulator, as it does not have it's own pin in the [Pin] section.  Rather, it is automatically included in the simulution when pins with Signal Names ending in "DTP or "DTN" are selected in the simulation tool.  See more under Note #4, "Pin Signal Name nomenclature" below.
					

# Input Termination Models

All models with Input Termination (IN25, IN50, IN75, and IN50M) are input-only (reciever) models.  If the actual pin is a bidirectional pin, when you want to simulate it as a driver, you will need to change the model to the appropriate selection that doesn't specify Input Termination, but rather does specify the drive class.  

Example: a bidirectional pins is set up with: SSTL18, Class-II, in bank-1 (Right side), Vccaux=2.5, IN_TERM=UNTUNED_SPLIT_75.  

To model the pin as a driver, you would use the SSTL18_II_LR_25 Model.  
To model the pin as a reciever, you would use the SSTL18_IN75_LR_25 Model.


# Output Termination Models

For the models with Output Termination (OT25, OT50, OT75), the Output Termination value will over-ride the driver class that the I/O was originally configured for (example: SSTL18 Class-I or Class-II), therefore the Model name does not include the driver Class.  So, for example, regardless if one I/O was initially configured as SSTL18, Class-I, Left or Right bank, Vccaux=2.5V, OUT_TERM=UNTUNED_50, and another I/O was configured identically except Class-II, they would both use the same IBIS Model: SSTL18_OT50_LR_25.


# Other Example Model names	
			
 1)LVCMOS33, 16 drive strength, QuietIO, Top Bottom bank, Vccaux=2.5V:  Model name: LVCMOS33_F_16_TB_25					
 2)PCI33_3, Left/Right bank, Vccaux=3.3V:                               Model name: PCI33_3_LR_33					
 3)HSTL, Class-III, Vcco=1.5V, Top/Bottom bank, Vccaux=2.5V:            Model name: HSTL_III_TB_25					
 4)HSTL, Class-III, Vcco=1.8V, Top/Bottom bank, Vccaux=3.3V:            Model name: HSTL_III_18_TB_33					


4. Pin Signal Name Nomenclature

The Pin Signal Name nomenclature is similar to the Model naming nomenclature, with some additions for the differential and pseudo-differential signals.  Pins for both differential and pseudo-differential signals will have the very last character as either "N" or "P". 
Pins with pseudo-differential IO standards will also have the first two characters as "D_". (D for Differential).
Full Differential I/O standards such as LVDS, PPDS, and RSDS can have an optional differential termination resistor enabled accross the N and P pins when the signals are inputs (recievers).  The model of those resistors is listed in the [Model] section, as "rtermxx_100_yy", where xx is the Vcco level, and yy is the Vccaux level.  To model pins with the optional differential termination resistor in the simulations, simply select the pins in the [Pin] section with "DTP" and "DTP" near the end of the signal_name.  Example: LVDS_25_TB_25_DTP.  These pins will automatically call up the (parallel) differential termination resistor via the use of the [Series Pin Mapping] section.  The DTN and DTP pins should only be used when the I/O is used as an input (reciever).  Select the non "DT" versions when the I/O is an output (driver).
Some parts of the name may be shortened so as to comply with the 20 character string limit in the IBIS 3.2 standard. Example: "IN50M" was compressed to "I50M" for the pin name "D_SSTL18_I50M_LR_25P".



*** Additional Resources

Official IBIS Home Page: 
http://www.eigroup.org/ibis/ibis.htm

Signal Integrity on Xilinx.com:
http://www.xilinx.com/products/design_resources/signal_integrity/index.htm


*** Revision History

1.1	7/27/09
	First published Spartan-6 IBIS models.
	
1.2     10/07/09
        Updated BLVDS_25_LR_25, BLVDS_25_LR_33, BLVDS_25_TB_25, BLVDS_25_TB_33, MINI_LVDS_25_TB_25, MINI_LVDS_25_TB_33, PCI66_3_LR_25 and PCI33_3_LR_25 models.
        Also updated LVDS_25_TB_25, LVDS_25_TB_33, LVDS_33_TB_25, LVDS_33_TB_33 and RSDS_33_TB_33 models
        
1.3	03/23/10
	Added TML_33_TB_25 and TML_33_TB_33 models
	Updated SSTL18_XX_XX_XX models for voltage range
	Updated HSTL_III_LR_25 model
        Added additional packages, and updated existing package RLC data in the [Package] section
										