---
title: Kontejnerizace aplikace s využitím kurzu Docker
description: V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 81b3ce2d6ebb73648d9026c92f490dcc723014f6
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331042"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="8192e-103">Kurz: Kontejnerizace aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="8192e-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="8192e-104">V tomto kurzu se naučíte, jak vytvořit image Docker, která obsahuje vaši aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8192e-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="8192e-105">Image se dá použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="8192e-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="8192e-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="8192e-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8192e-107">Vytvoření a publikování jednoduché aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="8192e-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="8192e-108">Vytvoření a konfigurace souboru Dockerfile pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="8192e-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="8192e-109">Sestavení image Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-109">Build a Docker image</span></span>
> * <span data-ttu-id="8192e-110">Vytvoření a spuštění kontejneru Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-110">Create and run a Docker container</span></span>

<span data-ttu-id="8192e-111">Porozumíte sestavení kontejneru Docker a nasazování úloh pro aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8192e-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="8192e-112">*Platforma Docker* používá *modul Docker* k rychlému sestavování a zabalení aplikací jako *imagí Docker*.</span><span class="sxs-lookup"><span data-stu-id="8192e-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="8192e-113">Tyto image jsou napsané ve formátu *souboru Dockerfile* , aby je bylo možné nasadit a spustit v vrstveném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8192e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8192e-114">Prerequisites</span></span>

<span data-ttu-id="8192e-115">Nainstalujte následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="8192e-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="8192e-116">[Sada .NET Core 2,2 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="8192e-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="8192e-117">Pokud máte nainstalované rozhraní .NET Core, pomocí `dotnet --info` příkazu určete, kterou sadu SDK používáte.</span><span class="sxs-lookup"><span data-stu-id="8192e-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="8192e-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="8192e-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="8192e-119">Dočasná pracovní složka pro *souboru Dockerfile* a ukázkovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8192e-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="8192e-120">V tomto kurzu se název `docker-working` používá jako pracovní složka.</span><span class="sxs-lookup"><span data-stu-id="8192e-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="8192e-121">Použít sadu SDK verze 2,2</span><span class="sxs-lookup"><span data-stu-id="8192e-121">Use SDK version 2.2</span></span>

<span data-ttu-id="8192e-122">Pokud používáte sadu SDK, která je novější, třeba 3,0, ujistěte se, že je aplikace nucená používat sadu SDK sady 2,2.</span><span class="sxs-lookup"><span data-stu-id="8192e-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="8192e-123">Vytvořte v pracovní složce `global.json` soubor s názvem a vložte do něj následující kód JSON:</span><span class="sxs-lookup"><span data-stu-id="8192e-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="8192e-124">Soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="8192e-124">Save this file.</span></span> <span data-ttu-id="8192e-125">Přítomnost souboru vynutí, aby rozhraní .NET Core používalo verzi 2,2 pro `dotnet` jakýkoli příkaz nazvaný z této složky a níže.</span><span class="sxs-lookup"><span data-stu-id="8192e-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="8192e-126">Vytvoření aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="8192e-126">Create .NET Core app</span></span>

<span data-ttu-id="8192e-127">Potřebujete aplikaci .NET Core, kterou bude kontejner Docker spustit.</span><span class="sxs-lookup"><span data-stu-id="8192e-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="8192e-128">Otevřete terminál, vytvořte pracovní složku, pokud jste to ještě neudělali, a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="8192e-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="8192e-129">V pracovní složce spusťte následující příkaz, který vytvoří nový projekt v podadresáři s názvem App:</span><span class="sxs-lookup"><span data-stu-id="8192e-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="8192e-130">Váš strom složek bude vypadat následovně:</span><span class="sxs-lookup"><span data-stu-id="8192e-130">Your folder tree will look like the following:</span></span>

```console
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="8192e-131">Příkaz vytvoří novou složku s názvem App a vygeneruje aplikaci Hello World.  `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="8192e-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="8192e-132">Zadejte složku *aplikace* a spusťte příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="8192e-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="8192e-133">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8192e-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="8192e-134">Výchozí šablona vytvoří aplikaci, která se vytiskne do terminálu a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="8192e-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="8192e-135">V tomto kurzu použijete aplikaci, která bude mít neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="8192e-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="8192e-136">V textovém editoru otevřete soubor **program.cs** .</span><span class="sxs-lookup"><span data-stu-id="8192e-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="8192e-137">V současné době by měl vypadat jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8192e-137">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="8192e-138">Nahraďte soubor následujícím kódem, který počítá čísla každou sekundu:</span><span class="sxs-lookup"><span data-stu-id="8192e-138">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="8192e-139">Uložte soubor a otestujte program znovu pomocí `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="8192e-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="8192e-140">Mějte na paměti, že tato aplikace bude běžet po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="8192e-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="8192e-141">K zastavení použijte příkaz zrušit <kbd>CTRL + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="8192e-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="8192e-142">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8192e-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="8192e-143">Pokud předáte číslo do příkazového řádku do aplikace, bude se počítat jenom s touto velikostí a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="8192e-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="8192e-144">Zkuste to s `dotnet run -- 5` počtem až pěti.</span><span class="sxs-lookup"><span data-stu-id="8192e-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="8192e-145">Jakékoli parametry po `--` nejsou předány `dotnet run` do příkazu a místo toho jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="8192e-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="8192e-146">Publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="8192e-146">Publish .NET Core app</span></span>

<span data-ttu-id="8192e-147">Před přidáním aplikace .NET Core do image Docker ji publikujte.</span><span class="sxs-lookup"><span data-stu-id="8192e-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="8192e-148">Chcete se ujistit, že kontejner spouští publikovanou verzi aplikace, když je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="8192e-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="8192e-149">Z pracovní složky zadejte složku **aplikace** s příkladem zdrojového kódu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8192e-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="8192e-150">Tento příkaz zkompiluje vaši aplikaci do složky pro **publikování** .</span><span class="sxs-lookup"><span data-stu-id="8192e-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="8192e-151">Cesta ke složce pro **publikování** z pracovní složky by měla být`.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="8192e-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="8192e-152">Získejte výpis adresáře složky pro publikování a ověřte, zda byla vytvořena aplikace **MyApp. dll** .</span><span class="sxs-lookup"><span data-stu-id="8192e-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="8192e-153">Ve složce **aplikace** spusťte jeden z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="8192e-153">From the **app** folder, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="8192e-154">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="8192e-154">Create the Dockerfile</span></span>

<span data-ttu-id="8192e-155">Soubor *souboru Dockerfile* používá `docker build` příkaz k vytvoření image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="8192e-156">Tento soubor je soubor ve formátu prostého textu s názvem *souboru Dockerfile* , který nemá příponu.</span><span class="sxs-lookup"><span data-stu-id="8192e-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="8192e-157">V terminálu přejděte v adresáři do pracovní složky, kterou jste vytvořili na začátku.</span><span class="sxs-lookup"><span data-stu-id="8192e-157">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="8192e-158">Vytvořte v pracovní složce soubor s názvem *souboru Dockerfile* a otevřete ho v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="8192e-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="8192e-159">Jako první řádek souboru přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8192e-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="8192e-160">Příkaz instruuje Docker, aby vyčetl obrázek s příznakem **2,2** z úložiště **MCR.Microsoft.com/dotnet/Core/Runtime.** `FROM`</span><span class="sxs-lookup"><span data-stu-id="8192e-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="8192e-161">Ujistěte se, že vyžádáte modul runtime .NET Core, který odpovídá modulu runtime, který cílí na vaši sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="8192e-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="8192e-162">Například aplikace vytvořená v předchozí části používala sadu .NET Core 2,2 SDK a vytvořila aplikaci cílenou na rozhraní .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="8192e-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="8192e-163">Základní bitová kopie, na kterou odkazuje *souboru Dockerfile* , je označená jako **2,2**.</span><span class="sxs-lookup"><span data-stu-id="8192e-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="8192e-164">Uložte soubor *souboru Dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="8192e-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="8192e-165">Adresářová struktura pracovní složky by měla vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="8192e-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="8192e-166">Některé soubory hlubší úrovně a složky byly vyjmuty, aby se ušetřilo místo v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="8192e-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```console
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="8192e-167">Z terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="8192e-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="8192e-168">Docker zpracuje každý řádek v *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="8192e-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="8192e-169">V příkazu dá Docker pokyn k použití aktuální složky k vyhledání *souboru Dockerfile.* `.` `docker build`</span><span class="sxs-lookup"><span data-stu-id="8192e-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="8192e-170">Tento příkaz sestaví image a vytvoří místní úložiště s názvem **MyImage** , které odkazuje na tuto image.</span><span class="sxs-lookup"><span data-stu-id="8192e-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="8192e-171">Po dokončení tohoto příkazu spusťte `docker images` příkaz a zobrazí se seznam nainstalovaných imagí:</span><span class="sxs-lookup"><span data-stu-id="8192e-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="8192e-172">Všimněte si, že tyto dva obrázky sdílejí stejnou hodnotu **ID obrázku** .</span><span class="sxs-lookup"><span data-stu-id="8192e-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="8192e-173">Tato hodnota je stejná mezi oběma obrazci, protože jediný příkaz v *souboru Dockerfile* byl založen na novém obrázku na stávající imagi.</span><span class="sxs-lookup"><span data-stu-id="8192e-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="8192e-174">Pojďme do *souboru Dockerfile*přidat dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="8192e-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="8192e-175">Každý příkaz vytvoří novou vrstvu obrázku s posledním příkazem reprezentujícím obrázek, na který bude **MyImage** úložiště odkazovat.</span><span class="sxs-lookup"><span data-stu-id="8192e-175">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="8192e-176">`COPY` Příkaz vyzve Docker ke zkopírování zadané složky ve vašem počítači do složky v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="8192e-177">V tomto příkladu je složka pro **publikování** zkopírována do složky s názvem **App** v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-177">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="8192e-178">Následující příkaz `ENTRYPOINT`instruuje Docker ke konfiguraci kontejneru tak, aby běžel jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="8192e-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="8192e-179">Po spuštění `ENTRYPOINT` kontejneru se příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="8192e-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="8192e-180">Po ukončení tohoto příkazu se kontejner automaticky zastaví.</span><span class="sxs-lookup"><span data-stu-id="8192e-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="8192e-181">V terminálu spusťte `docker build -t myimage -f Dockerfile .` příkaz a po jeho dokončení spusťte `docker images`příkaz.</span><span class="sxs-lookup"><span data-stu-id="8192e-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="8192e-182">Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořila **ID obrázku**.</span><span class="sxs-lookup"><span data-stu-id="8192e-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="8192e-183">Konečné **ID image** (bude se lišit) bude **ddcc6646461b** a dál vytvoříte kontejner na základě tohoto obrázku.</span><span class="sxs-lookup"><span data-stu-id="8192e-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="8192e-184">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="8192e-184">Create a container</span></span>

<span data-ttu-id="8192e-185">Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="8192e-186">Kontejner můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="8192e-186">You can create a container in two ways.</span></span> <span data-ttu-id="8192e-187">Nejdřív vytvořte nový kontejner, který se zastaví.</span><span class="sxs-lookup"><span data-stu-id="8192e-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="8192e-188">Výše uvedený příkaz vytvoří kontejner založený na imagi **MyImage.** `docker create`</span><span class="sxs-lookup"><span data-stu-id="8192e-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="8192e-189">Výstup tohoto příkazu ukazuje **ID kontejneru** (bude se lišit) vytvořeného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="8192e-190">Chcete-li zobrazit seznam *všech* kontejnerů, použijte `docker ps -a` příkaz:</span><span class="sxs-lookup"><span data-stu-id="8192e-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="8192e-191">Správa kontejneru</span><span class="sxs-lookup"><span data-stu-id="8192e-191">Manage the container</span></span>

<span data-ttu-id="8192e-192">Každému kontejneru je přiřazen náhodný název, který můžete použít k odkazování na tuto instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="8192e-193">Například kontejner, který byl vytvořen automaticky, zvolil název **boring_matsumoto** (bude jiný a tento název lze použít ke spuštění kontejneru).</span><span class="sxs-lookup"><span data-stu-id="8192e-193">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="8192e-194">Automatický název přepíšete pomocí konkrétního `docker create --name` parametru.</span><span class="sxs-lookup"><span data-stu-id="8192e-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="8192e-195">Následující příklad používá `docker start` příkaz ke spuštění kontejneru a poté `docker ps` používá příkaz k zobrazení pouze kontejnerů, které jsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="8192e-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="8192e-196">`docker stop` Podobně příkaz zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="8192e-197">Následující příklad používá `docker stop` příkaz k zastavení kontejneru a poté `docker ps` používá příkaz k zobrazení, že žádné kontejnery neběží.</span><span class="sxs-lookup"><span data-stu-id="8192e-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="8192e-198">Připojit ke kontejneru</span><span class="sxs-lookup"><span data-stu-id="8192e-198">Connect to a container</span></span>

<span data-ttu-id="8192e-199">Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="8192e-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="8192e-200">Použijte příkazy `docker attach` a ke spuštění kontejneru a k prohlížení výstupního datového proudu. `docker start`</span><span class="sxs-lookup"><span data-stu-id="8192e-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="8192e-201">V tomto příkladu se k odpojení od běžícího kontejneru používá příkaz <kbd>CTRL + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="8192e-201">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="8192e-202">To může ve skutečnosti ukončit proces v kontejneru, který zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-202">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="8192e-203">Parametr zajistí, že <kbd>CTRL + C</kbd> nezastaví proces v kontejneru. `--sig-proxy=false`</span><span class="sxs-lookup"><span data-stu-id="8192e-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="8192e-204">Po odpojení od kontejneru znovu připojte, abyste ověřili, že pořád běží a počítá se.</span><span class="sxs-lookup"><span data-stu-id="8192e-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="8192e-205">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="8192e-205">Delete a container</span></span>

<span data-ttu-id="8192e-206">Pro účely tohoto článku nechcete, aby kontejnery právě neprováděly žádné akce.</span><span class="sxs-lookup"><span data-stu-id="8192e-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="8192e-207">Odstraňte kontejner, který jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="8192e-207">Delete the container you previously created.</span></span> <span data-ttu-id="8192e-208">Pokud je kontejner spuštěný, zastavte ho.</span><span class="sxs-lookup"><span data-stu-id="8192e-208">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="8192e-209">Následující příklad zobrazí seznam všech kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="8192e-209">The following example lists all containers.</span></span> <span data-ttu-id="8192e-210">Pak pomocí příkazu tento `docker rm` kontejner odstraní a pak u všech spuštěných kontejnerů zkontroluje druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="8192e-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="8192e-211">Jeden běh</span><span class="sxs-lookup"><span data-stu-id="8192e-211">Single run</span></span>

<span data-ttu-id="8192e-212">Docker poskytuje `docker run` příkaz pro vytvoření a spuštění kontejneru jako jediného příkazu.</span><span class="sxs-lookup"><span data-stu-id="8192e-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="8192e-213">Tento příkaz eliminuje nutnost spuštění `docker create` a pak. `docker start`</span><span class="sxs-lookup"><span data-stu-id="8192e-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="8192e-214">Tento příkaz lze také nastavit tak, aby při zastavení kontejneru automaticky odstranil kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="8192e-215">Například použijte `docker run -it --rm` k provedení dvou věcí, nejdřív, automatické použití aktuálního terminálu k připojení ke kontejneru a po dokončení kontejneru ho odeberte:</span><span class="sxs-lookup"><span data-stu-id="8192e-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="8192e-216">V `docker run -it`systému, příkaz <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, který zase zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="8192e-217">Vzhledem k `--rm` tomu, že byl zadán parametr, kontejner je automaticky odstraněn při zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="8192e-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="8192e-218">Ověřte, že neexistuje:</span><span class="sxs-lookup"><span data-stu-id="8192e-218">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="8192e-219">Změnit vstupní bod</span><span class="sxs-lookup"><span data-stu-id="8192e-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="8192e-220">Příkaz také umožňuje `ENTRYPOINT` upravit příkaz z souboru Dockerfile a spustit něco jiného, ale pouze pro tento kontejner.  `docker run`</span><span class="sxs-lookup"><span data-stu-id="8192e-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="8192e-221">Například použijte následující příkaz ke spuštění `bash` nebo. `cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="8192e-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="8192e-222">V případě potřeby upravte příkaz.</span><span class="sxs-lookup"><span data-stu-id="8192e-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="8192e-223">Windows</span><span class="sxs-lookup"><span data-stu-id="8192e-223">Windows</span></span>
<span data-ttu-id="8192e-224">V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="8192e-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="8192e-225">Stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončíte proces a zastavíte kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-225"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a><span data-ttu-id="8192e-226">Linux</span><span class="sxs-lookup"><span data-stu-id="8192e-226">Linux</span></span>

<span data-ttu-id="8192e-227">V tomto příkladu `ENTRYPOINT` se změní na `bash`.</span><span class="sxs-lookup"><span data-stu-id="8192e-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="8192e-228">`quit` Příkaz se spustí, který ukončí proces a zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="8192e-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="8192e-229">Důležité příkazy</span><span class="sxs-lookup"><span data-stu-id="8192e-229">Essential commands</span></span>

<span data-ttu-id="8192e-230">Docker má mnoho různých příkazů, které pokrývají, co chcete s kontejnerem a obrázky udělat.</span><span class="sxs-lookup"><span data-stu-id="8192e-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="8192e-231">Tyto příkazy Docker jsou zásadní pro správu vašich kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="8192e-231">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="8192e-232">sestavení Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="8192e-233">spuštění Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="8192e-234">Docker PS</span><span class="sxs-lookup"><span data-stu-id="8192e-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="8192e-235">zastavení Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="8192e-236">Docker RM</span><span class="sxs-lookup"><span data-stu-id="8192e-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="8192e-237">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="8192e-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="8192e-238">Obrázek Docker</span><span class="sxs-lookup"><span data-stu-id="8192e-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="8192e-239">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="8192e-239">Clean up resources</span></span>

<span data-ttu-id="8192e-240">V tomto kurzu jste vytvořili kontejnery a image.</span><span class="sxs-lookup"><span data-stu-id="8192e-240">During this tutorial you created containers and images.</span></span> <span data-ttu-id="8192e-241">Pokud chcete, tyto prostředky odstraňte.</span><span class="sxs-lookup"><span data-stu-id="8192e-241">If you want, delete these resources.</span></span> <span data-ttu-id="8192e-242">Následující příkazy použijte k</span><span class="sxs-lookup"><span data-stu-id="8192e-242">Use the following commands to</span></span>

01. <span data-ttu-id="8192e-243">Vypsat všechny kontejnery</span><span class="sxs-lookup"><span data-stu-id="8192e-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="8192e-244">Zastavte kontejnery, které jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="8192e-244">Stop containers that are running.</span></span> <span data-ttu-id="8192e-245">`CONTAINER_NAME` Představuje název automaticky přiřazený kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8192e-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="8192e-246">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="8192e-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="8192e-247">Pak na počítači odstraňte všechny image, které už nechcete.</span><span class="sxs-lookup"><span data-stu-id="8192e-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="8192e-248">Odstraňte image vytvořenou *souboru Dockerfile* a pak odstraňte image .NET Core, na které byl *souboru Dockerfile* založen.</span><span class="sxs-lookup"><span data-stu-id="8192e-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="8192e-249">Můžete použít **ID obrázku** nebo **úložiště:** řetězec ve formátu značek.</span><span class="sxs-lookup"><span data-stu-id="8192e-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="8192e-250">`docker images` Pomocí příkazu zobrazte seznam nainstalovaných imagí.</span><span class="sxs-lookup"><span data-stu-id="8192e-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="8192e-251">Soubory obrázků můžou být velké.</span><span class="sxs-lookup"><span data-stu-id="8192e-251">Image files can be large.</span></span> <span data-ttu-id="8192e-252">Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8192e-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="8192e-253">Při plánování vytváření dalších imagí na základě tohoto modulu runtime obvykle zachováte základní image s nainstalovaným modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="8192e-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8192e-254">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8192e-254">Next steps</span></span>

* [<span data-ttu-id="8192e-255">Vyzkoušejte si kurz ASP.NET Core mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="8192e-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="8192e-256">Projděte si služby Azure, které podporují kontejnery.</span><span class="sxs-lookup"><span data-stu-id="8192e-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* [<span data-ttu-id="8192e-257">Přečtěte si o příkazech souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8192e-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
* [<span data-ttu-id="8192e-258">Prozkoumejte nástroje kontejnerů pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8192e-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
