# Develop a new standard library using `zos`

**ZeppelinOS** handles releases of the standard library. Any developer can publish new stdlib releases. The *zos* CLI allows developers to go through this process seamlessly, by creating packages that handle the different releases of the stdlib. 

The first step is creating a package with the following command:
```
zos init --lib <package-name>
```
Initializing the package will create a `package.zos.json` file that tracks the contracts included in the standard library release. After this first step, the desired contracts must be individually added to the package through:
```
zos add <contract-name>,
```
where `<contract-name>` is the name of the contract. Note that this command must be repeated once for each contract included in the package. This will update the `package.zos.json` file with the contract names. 

Finally, we need to deploy the `Package`, the `Release` containing the stdlib, and the individual library contracts. All of this is accomplished by:
```
zos push --lib --network=<network>.
```
This command creates a file `package.zos.<network>.json` that, apart from the included contracts, has the address of the `Package`. This completes the deployment of the new stdlib release to the chosen network.

Send your standard library release address to other developers to get them to use it!