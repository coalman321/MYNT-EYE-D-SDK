Update Auxiliary Chip Firmware
===============================

Get Auxiliary Chip Firmware
----------------------------

Latest firmware: MYNTEYE-D1000-auxiliary-chip-x.x.x.bin `Google
Drive <https://drive.google.com/open?id=1gAbTf6W10a8iwT7L9TceMVgxQCWKnEsx>`__,
`Baidu Pan <https://pan.baidu.com/s/1sZKxugg5P8Dk5QgneA9ttw>`__

Compile SDK Samples
-----------------

.. code-block:: bash

   cd <sdk>  # local path of SDK
   make samples

Update Firmware
---------------

.. code-block:: bash

   ./samples/_output/bin/writer/auxiliary_firmware_update <firmware-file-path>
