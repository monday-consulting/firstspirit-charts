# FirstSpirit Helm Charts

THIS PROJECT IS NOT AN OFFICIAL PRODUCT BY [Crownpeak Technology GmbH](https://www.e-spirit.com/). It is maintained and
provided by [Monday Consulting](https://www.monday-consultig.com/) to the FirstSpirit Community

## What is FirstSpirit

> FirstSpirit ist ein kommerzielles Content-Management-System, das von der
> Dortmunder [Crownpeak Technology GmbH](https://www.e-spirit.com/), einem Tochterunternehmen der CrownPeak Inc., seit
> 1999 entwickelt wurde. Die erste stabile Version 0.9 wurde am 7. Juni 2000 herausgegeben. Das System ist in Java
> entwickelt und wird für GNU/Linux, Solaris (x86, Sparc), AIX und Windows angeboten.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

`helm repo add firstspirit-charts https://monday-consulting.github.io/firstspirit-charts`

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
firstspirit-charts` to see the charts.

To install the <chart-name> chart:

    helm install my-<chart-name> firstspirit-charts/<chart-name>

To uninstall the chart:

    helm delete my-<chart-name>

## Charts in this repo

See the readme files of the charts for further information

* [firstspirit](/charts/firstspirit/README.md)

## Legal Notices

FirstSpirit is a product of [Crownpeak Technology GmbH](https://www.e-spirit.com/), Dortmund, Germany.

## Disclaimer

This document is provided for information purposes only. Monday Consulting may change the contents hereof without
notice. This document is not warranted to be error-free, nor subject to any other warranties or conditions, whether
expressed orally or implied in law, including implied warranties and conditions of merchantability or fitness for a
particular purpose. Monday Consulting specifically disclaims any liability with respect to this document and no
contractual obligations are formed either directly or indirectly by this document. The technologies, functionality,
services, and processes described herein are subject to change without notice.