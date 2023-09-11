## IBM watsonx.data
IBM® watsonx.data is a new open architecture lakehouse that combines the elements of the data warehouse and data lakes. The best-in-class features and optimizations available on the watsonx.data make it an optimal choice for next generation data analytics and automation. It offers a single platform where you can attach data residing in object store and relational databases, synthesize the data through a SQL interface and make the data available for AI and BI applications.


## IBM watsonx.data client package
The watsonx.data client package includes convenient utilities and pre-packaged libraries to access and develop applications that work with IBM watsonx.data.

## Installing watsonx.data client package
To install watsonx.data client package, you will need the ibm-lh-client.tgz and the container images.

### Before you begin
1. Setup a single-node virtual machine to install the package. The supported operating system environments are
- Linux
- Windows
- Mac OS x86
- Mac with Apple Silicon with Rosetta. For more information, see https://ibmdocs-test.dcs.ibm.com/docs/en/lakehouse_test?topic=version-prerequisites-watsonxdata-installation-mac
2. Determine the version of watsonx.data that you want to install, and transfer the ibm-lh-client-*.tgz file to the machine, say to `/tmp`
2. Install `docker` or `podman` to run the container images. 
3. Install `podman-plugins` (`yum install podman-plugins`). It is important that you install `podman-plugins` before intalling watsonx.data.
3. Procure the read key to access the container images which are hosted in a container registry within IBM. You can get the read key by signing up for the Academic Initiative (link to Academic Initiative portal), or the Partner program (link to Partner World portal)

### Procedure
1. Set up the installation directory and environment variables

a. Set up the work directory.
   ```
   mkdir <install_directory>
   cd <install_directory>
   ```
b. Extract the client package
   ```
   tar -xvf /tmp/ibm-lh-client-*.tgz
   ```
   This will create a directory by the name `ibm-lh-client`
c. Review the license files located under `<install_directory>/ibm-lh-client`

2. Set the environment variables
   ```
   export LH_REGISTRY=icr.io/watsonx_data_dev_client_pkg
   ```

3. Authenticate to the container registry
   ```
   docker login $LH_REGISTRY -u iamapikey -p <read key procured from IBM>
   ```
4. Optional: You can customize your installation by editting the values in `ibm-lh-client/etc/launch_config.env`
5. Run the setup script
   ```
   ibm-lh-dev/bin/setup --license_acceptance=y --runtime=docker
   ```
   or
   ```
   ibm-lh-dev/bin/setup --license_acceptance=y --runtime=podman
   ```
   This will pull the images from the container registry and start the container.

### Using the client package
