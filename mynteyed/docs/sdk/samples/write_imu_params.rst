.. _write_imu_params:

Write IMU Parameters
====================

SDK provides the tool ``imu_params_writer`` to write IMU parameters.

Information about how to get IMU parameters, please read :ref:`get_imu_params` .

Reference commands:

.. code-block:: bash

   ./samples/_output/bin/writer/imu_params_writer samples/writer/config/imu.params

   # Windows
   .\samples\_output\bin\writer\imu_params_writer.bat samples\writer\config\imu.params

The path of parameters file can be found in
`samples/writer/config/imu.params <https://github.com/slightech/MYNT-EYE-D-SDK/blob/master/samples/writer/config/imu.params>`__
. If you calibrated the parameters yourself, you can edit the file and
run above commands to write them into the device.

   Warning - Please don’t override parameters, you can use
   ``save_all_infos`` to backup parameters.

Complete code samples，see
`imu_params_writer.cc <https://github.com/slightech/MYNT-EYE-D-SDK/blob/master/samples/writer/imu_params_writer.cc>`__
.
