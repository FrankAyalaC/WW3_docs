.. Documentacion WAVEWATCH III documentation master file, created by
   sphinx-quickstart on Fri May 21 11:08:17 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to the WAVEWATCH III Online Tutorial!
=======================================================

WAVEWATCH III (WWIII) is a community wave modeling framework that includes the latest scientific advancements in the field of wind-wave modeling and dynamics. The core of the framework consists of the WAVEWATCH III third-generation wave model (WAVE-height, WATer depth and Current Hindcasting), developed at NOAA/NCEP.

WWIII solves the random phase spectral action density balance equation for wavenumber-direction spectra. The implicit assumption of this equation is that properties of medium (water depth and current) as well as the wave field itself vary on time and space scales that are much larger than the variation scales of a single wave. The model includes options for shallow-water (surf zone) applications, as well as wetting and drying of grid points. The wave model is a sophisticated modeling system with numerous developments that have been added in recent years (wave – hurricane interaction physics, new wave growth and dissipation physics packages, wave – mud, wave – vegetation and wave – bottom interaction physics to name a few) that make this model attractive for this project.  Propagation of a wave spectrum can be solved using regular (rectilinear or curvilinear) and unstructured (triangular) grids.

WWIII is also used to model atmosphere-ocean interactions with the OWA (Ocean-Wave-Atmosphere) modelling system. Due to a diferent capabilites of coupling with atmosphere models (i.e WRF) and ocean models (i.e CROCO, NEMO,etc), this model is widely used by the community climate modelling. 

This tutorial were created with the WWIII v6.07 and is designed to take you through this amazing wave model, step by step. Simply follow the tutorial flow (read de table of contents)

Please, look out all signs that showed along the tutorial:

.. note:: 

   This is note text. Use a note for information you want the user to
   pay particular attention to.

.. hint::

	hint/tip/important are similar

	We recommend that you work through the tutorial examples before you try to run WRF ARW on your own.

.. warning::

	Warning/caution/attention are similar

	This is warning text. Use a warning for information the user must understand to avoid negative consequences.

.. danger::
	
	danger/error are similar

	This is a new tip, wonderful!


**Let's go to model and ride the wave with us!**

.. toctree::
    :maxdepth: 2
    :caption: Contents:

    sys_req
    get_model
    init_commands
    environment
    contains_compilation
    test_cases
    prep_conf
    compilation
    preprocessing
    exe_model

Disclaimer
**********

This tutorial is not intended to supplant the official WW3 documentation

Comments/help
*************

If you have questions regarding WAVEWATCH III, or problems with this Online Tutorial, please let us know them in WWIII Forum (Link) or in the email something@gmail.com
