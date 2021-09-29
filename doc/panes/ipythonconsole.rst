

   .. image:: /images/console/console-connect-local-step2.gif
      :alt: Copying the connection filename into Spyder's dialog

#. Click :guilabel:`OK` to connect to the kernel.

   .. image:: /images/console/console-connect-local-step3.gif
      :alt: Connecting to the kernel and running basic commands.


Connect to a remote kernel
~~~~~~~~~~~~~~~~~~~~~~~~~~

To connect to a kernel on a remote machine,

#. Launch a Spyder kernel on the remote host if one is not already running, with ``python -m spyder_kernels.console``.

   .. image:: /images/console/console-connect-remote-step1.gif
      :alt: Staring a Spyder kernel on a remote machine

#. Copy the kernel's connection file (:file:`{jupyter/runtime/dir/path}/kernel-{pid}.json`) to the machine you're running Spyder on.

   You can get :file:`{jupyter/runtime/dir/path}` by executing ``jupyter --runtime-dir`` in the same Python environment as the kernel.
   Usually, the connection file you are looking for will be one of the newest in this directory, corresponding to the time you started the external kernel.

   .. image:: /images/console/console-connect-remote-step2.gif
      :alt: Using SCP to copy the connection file to the local machine

#. Click :guilabel:`Connect to an existing kernel` from the :guilabel:`Consoles` menu, and browse for or enter the path to the connection file from the previous step.

   As a convenience, kernel ID numbers (e.g. ``1234``) entered in the connection file path field will be expanded to :file:`{jupyter/runtime/dir/path}/kernal-{id}.json` on your local machine, if you've copied the connection file there.

   .. image:: /images/console/console-connect-remote-step3.gif
      :alt: Opening the connect to kernel dialog and browsing for the path

#. Check the :guilabel:`This is a remote kernel (via SSH)` box and enter the :guilabel:`Hostname` or IP address, username and port to connect to on the remote machine.
   Then, enter *either* :file:`{username}`'s password on the remote machine, or browse to an SSH keyfile (typically in the :file:`.ssh` directory in your home folder on the local machine, often called :file:`id_rsa` or similar) registered on it; only one is needed to connect.
   If you check :guilabel:`Save connection settings`, these details will be remembered and filled for you automatically next time you open the dialog.

   Note that :guilabel:`Port` is the port number on your remote machine that the SSH daemon (``sshd``) is listening on, typically 22 unless you or your administrator has configured it otherwise.

   .. image:: /images/console/console-connect-remote-step4.gif
      :alt: Entering pre-filled SSH details into the connection dialog

#. Click :guilabel:`OK` to connect to the remote kernel

   .. image:: /images/console/console-connect-remote-step5.gif
      :alt: Connecting to the remote kernel and running basic commands

For more technical details about connecting to remote kernels, see the `Connecting to a remote kernel`_ page in the IPython Cookbook.

.. _Connecting to a remote kernel: https://github.com/ipython/ipython/wiki/Cookbook:-Connecting-to-a-remote-kernel-via-ssh



.. _umr-section:

======================
Reload changed modules
======================

When working in an interactive session, Python only loads a module from its source file once, the first time it is imported.

Spyder's :guilabel:`User Module Reloader` (UMR) automatically reloads modules right in your existing IPython consoles whenever they are modified and re-imported.
With the UMR enabled, you can test changes to your code without restarting the kernel.

.. image:: /images/console/console-reload-modules.png
   :alt: Spyder showing reloading modules in console

UMR is enabled by default, and it will provide you with a red ``Reloaded modules:`` message in the console listing the files it has refreshed when it is activated.
If desired, you can turn it on or off, and prevent specific modules from being reloaded, under :menuselection:`Preferences --> Python interpreter --> User Module Reloader (UMR)`.

.. image:: /images/console/console-umr-preferences.png
   :alt: Spyder preferences showing option to use module reloader



==================
Related components
==================

* :doc:`debugging`
* :doc:`editor`
* :doc:`help`
* :doc:`historylog`
* :doc:`variableexplorer`
