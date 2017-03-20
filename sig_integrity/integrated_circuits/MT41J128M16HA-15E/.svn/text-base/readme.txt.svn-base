V69A IBIS Model 
Die Rev D
2Gb DDR3 SDRAM IBIS models
Rev 2.1-05/11/2010

The v69a.ibs/v69a_it.ibs/v69a_at.ibs model includes On Die Termination (ODT) characteristics.  
ODT in DQ* models are modeled through the use of [Submodel] power and ground clamp I-V curves 
that add the termination characteristics to the regular power and ground clamp
characteristics when the I/O is functioning as an input. Use the [Model Selector] 
to choose between 20,30,40,60 and 120 ohm ODT settings.

NOTE: C_comp is different for the ODT-enabled models versus the normal I/O model.
The C_comp value is set to match the input state of the DQ I/O as measured from
the HSPICE model.  Due to the C_comp differences between the DQ model and the
DQ_ODT* models, the output characteristics of the models will look different
when simulated.  So, to match most closely with the HSPICE model, simulate with
the DQ_FULL or DQ_HALF model for ALL Output simulations.  Use the ODT models
ONLY for Input simulations. 

[Disclaimer]    This software code and all associated documentation, comments
                or other information (collectively "Software") is provided 
                "AS IS" without warranty of any kind. MICRON TECHNOLOGY, INC. 
                ("MTI") EXPRESSLY DISCLAIMS ALL WARRANTIES EXPRESS OR IMPLIED,
                INCLUDING BUT NOT LIMITED TO, NONINFRINGEMENT OF THIRD PARTY
                RIGHTS, AND ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS
                FOR ANY PARTICULAR PURPOSE. MTI DOES NOT WARRANT THAT THE
                SOFTWARE WILL MEET YOUR REQUIREMENTS, OR THAT THE OPERATION OF
                THE SOFTWARE WILL BE UNINTERRUPTED OR ERROR-FREE. FURTHERMORE,
                MTI DOES NOT MAKE ANY REPRESENTATIONS REGARDING THE USE OR THE
                RESULTS OF THE USE OF THE SOFTWARE IN TERMS OF ITS CORRECTNESS,
                ACCURACY, RELIABILITY, OR OTHERWISE. THE ENTIRE RISK ARISING OUT
                OF USE OR PERFORMANCE OF THE SOFTWARE REMAINS WITH YOU. IN NO
                EVENT SHALL MTI, ITS AFFILIATED COMPANIES OR THEIR SUPPLIERS BE
                LIABLE FOR ANY DIRECT, INDIRECT, CONSEQUENTIAL, INCIDENTAL, OR
                SPECIAL DAMAGES (INCLUDING, WITHOUT LIMITATION, DAMAGES FOR LOSS
                OF PROFITS, BUSINESS INTERRUPTION, OR LOSS OF INFORMATION)
                ARISING OUT OF YOUR USE OF OR INABILITY TO USE THE SOFTWARE,
                EVEN IF MTI HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.
                Because some jurisdictions prohibit the exclusion or limitation
                of liability for consequential or incidental damages, the above
                limitation may not apply to you.
 
                Copyright 2006 Micron Technology, Inc. All rights reserved.
