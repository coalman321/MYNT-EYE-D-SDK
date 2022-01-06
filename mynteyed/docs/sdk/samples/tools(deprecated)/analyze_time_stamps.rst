.. role:: raw-latex(raw)
   :format: latex
..

.. _analyze_time_stamps:

Analyze Time Stamps
===================

SDK provides a script for timestamp analysis stamp_analytics.py . Tool
details are visible in tools/README.md .

.. note::

  You need to use ``record`` tool in ``tools`` or ``rosbag`` to record dataset first.
  Timestamp analysis tool support python 2.7 .
  Before run the script, you need to ``pip install -r requirements.txt`` .

Reference run commands on Linux:

.. code-block:: bash

   $ python tools/analytics/stamp_analytics.py -i dataset -c tools/config/mynteye/mynteye_config.yaml

Reference to results on Linux:

.. code-block:: bash

   $ python tools/analytics/stamp_analytics.py -i dataset -c tools/config/mynteye/mynteye_config.yaml
   stamp analytics ...
     input: dataset
     outdir: dataset
   open dataset ...
   save to binary files ...
     binimg: dataset/stamp_analytics_img.bin
     binimu: dataset/stamp_analytics_imu.bin
     img: 1007, imu: 20040

   rate (Hz)
     img: 25, imu: 500
   sample period (s)
     img: 0.04, imu: 0.002

   diff count
     imgs: 1007, imus: 20040
     imgs_t_diff: 1006, imus_t_diff: 20039

   diff where (factor=0.1)
     imgs where diff > 0.04*1.1 (0)
     imgs where diff < 0.04*0.9 (0)
     imus where diff > 0.002*1.1 (0)
     imus where diff < 0.002*0.9 (0)

   image timestamp duplicates: 0

   save figure to:
     dataset/stamp_analytics.png
   stamp analytics done

The analysis result graph will be saved in the dataset directory. as
follow:

.. figure:: ../../static/images/sdk/tools/stamp_analytics.png
   :alt: stamp analytics


In addition, the script specific options can be executed -h to
understand:

.. code-block:: bash

   $ python tools/analytics/stamp_analytics.py -h

