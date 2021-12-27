#Core POC

# Reports ASP.NET Core samples

## Pre-requisite

* Install `.NET Core 2.1 SDK` from https://dotnet.microsoft.com/download/dotnet-core and run `dotnet --version` to check whether it is installed properly or not.

* Install gulp package with global access by executing the below command  and run `gulp -v` to check whether it is installed properly or not.

```cmd
npm install gulp -g
```


## Document Structure

    --> Controllers (1)
        --> CompanySalesController
        --> ProductLineSalesController
    --> Models (2)
    --> Views (3)
        --> CompanySales
            --> Index.cshtml
        --> ProductLineSales
            --> Index.cshtml
    --> wwwroot (4)
        --> samples.json (5)

(1). This is where our `Report Viewer controllers` should be placed.

Note: Controller should inherit `PreviewController` and the action method which returns `IActionResult` should be named `Index`. Refer the below snippet

```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;

namespace ReportsCoreSamples.Controllers
{
    public class ProductLineSalesController : PreviewController
    {
        public IActionResult Index()
        {
            return View();
        }
        
    }
}

```

(2). This is where our `Report Viewer Models` should be placed.


(3). This is where our `Report Viewer Views` should be placed.


(4). This is where our `Static files` should be placed.

(5). This is our sample configuration file.

```json
{
  "samples": [
    {
      "routerPath": "CompanySales",
      "sampleName": "Company Sales",
      "imageDetails": {
        "imageName": "company-sales.png",
        "isLandscape": true
      },
      "metaData": {
        "description": "This sample demonstrates the Sales data by year with grouping."
      }
    },
    {
      "routerPath": "ProductLineSales",
      "sampleName": "Product Line Sales",
      "imageDetails": {
        "imageName": "product-line-sales.png",
        "isLandscape": false
      },
      "metaData": {
        "description": "This sample demonstrates the cascading parameters support by listing the sub category products based on product category."
      }
    }
  ]
}

```
`samples` - This is an array which contains all samples information.

`routerPath` - This is the our controller className without Controller suffix.

`sampleName` - This is our sample name which will be rendered in table of contents.

`directoryName` - This is our sample directory name.

`imageDetails.imageName` - This is our sample image name which will be rendered in table of contents.

Note : keep your sample images in `wwwroots/assets/sidebar` folder.

`imageDetails.isLandscape` - if it is true, your sample image will be renderend in lansscape mode else it will be renderend in portrait mode.

`metaData.description` - This is our sample description.

## QuickStart 

After completing prerequisite steps, Follow the below steps to run Reports ASP.NET Core samples 

Clone the repo from https://gitlab.syncfusion.com/data-science/reports-aspcore-samples from `development` branch.

### Build the Application 

* Run `npm install` to install the client side packages.

* Run `gulp phantom-download` to download the phantomjs.exe into dependent location.

* Run `gulp build` to build the application.

### Running the App from command line interface

* Run `dotnet restore` to restore the nuget packages.

* Run `dotnet run` to serve the application.

### Running the App in Visual Studio 2017

* Open the solution file in Visual Studio 2017

* Press F5 or click the Run button in Visual Studio to run the application

## Hosting in IIS

* Make sure that you have enabled IIS feature. If not, enable that feature from `Turn windows feature on or off`.

* Install the .NET Core Hosting Bundle from the below link

https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-2.2.3-windows-hosting-bundle-installer

* Then, host your production files in IIS.

## Pre-requisite for Including New Image for New Report

kindly increase the background width `wwwroot/css/common/sidebar.css, wwwroot/css/common/writer.css` of css class 

Portrait: `.ej-sidebar-content .ej-sb-toc .ej-sb-toc-card .ej-portrait-img`,

 `.r-w-container .r-w-sample-container .r-w-sample.r-w-sample-portrait .r-w-sample-image` or


Landscape: `.ej-sidebar-content .ej-sb-toc .ej-sb-toc-card .ej-landscape-img`,

 `.r-w-container .r-w-sample-container .r-w-sample.r-w-sample-landscape .r-w-sample-image`
```cmd
background-height = current-height + 100%;
```
