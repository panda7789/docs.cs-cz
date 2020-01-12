---
title: Kontejnerizace aplikace s využitím kurzu Docker
description: V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17d3dfbe58770b19a75be1dad3ae03406584992c
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900116"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="a9d08-103">Kurz: kontejnerizace aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="a9d08-104">V tomto kurzu se naučíte, jak vytvořit image Docker, která obsahuje vaši aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="a9d08-105">Image se dá použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="a9d08-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="a9d08-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="a9d08-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a9d08-107">Vytvoření a publikování jednoduché aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="a9d08-108">Vytvoření a konfigurace souboru Dockerfile pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="a9d08-109">Sestavení image Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-109">Build a Docker image</span></span>
> - <span data-ttu-id="a9d08-110">Vytvoření a spuštění kontejneru Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-110">Create and run a Docker container</span></span>

<span data-ttu-id="a9d08-111">Porozumíte sestavení kontejneru Docker a nasazování úloh pro aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="a9d08-112">*Platforma Docker* používá *modul Docker* k rychlému sestavování a zabalení aplikací jako *imagí Docker*.</span><span class="sxs-lookup"><span data-stu-id="a9d08-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="a9d08-113">Tyto image jsou napsané ve formátu *souboru Dockerfile* , aby je bylo možné nasadit a spustit v vrstveném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!TIP]
> <span data-ttu-id="a9d08-114">Pokud pracujete se stávající aplikací ASP.NET Core, přečtěte si kurz o [tom, jak kontejnerizace ASP.NET Core aplikace](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="a9d08-114">If you're working with an existing ASP.NET Core application, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a9d08-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9d08-115">Prerequisites</span></span>

<span data-ttu-id="a9d08-116">Nainstalujte následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="a9d08-116">Install the following prerequisites:</span></span>

- <span data-ttu-id="a9d08-117">\ [SDK pro .NET Core 3,1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="a9d08-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)\</span></span>
<span data-ttu-id="a9d08-118">Pokud máte nainstalované rozhraní .NET Core, pomocí příkazu `dotnet --info` určete, kterou sadu SDK používáte.</span><span class="sxs-lookup"><span data-stu-id="a9d08-118">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="a9d08-119">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="a9d08-119">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="a9d08-120">Dočasná pracovní složka pro *souboru Dockerfile* a ukázkovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-120">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="a9d08-121">V tomto kurzu použijete jako pracovní složku název *Docker – Work* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-121">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="a9d08-122">Vytvoření aplikace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-122">Create .NET Core app</span></span>

<span data-ttu-id="a9d08-123">Potřebujete aplikaci .NET Core, kterou bude kontejner Docker spustit.</span><span class="sxs-lookup"><span data-stu-id="a9d08-123">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="a9d08-124">Otevřete terminál, vytvořte pracovní složku, pokud jste to ještě neudělali, a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="a9d08-124">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="a9d08-125">V pracovní složce spusťte následující příkaz, který vytvoří nový projekt v podadresáři s názvem *App*:</span><span class="sxs-lookup"><span data-stu-id="a9d08-125">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="a9d08-126">Váš strom složek bude vypadat následovně:</span><span class="sxs-lookup"><span data-stu-id="a9d08-126">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="a9d08-127">Příkaz `dotnet new` vytvoří novou složku s názvem *App* a vygeneruje aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="a9d08-127">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="a9d08-128">Zadejte složku *aplikace* a spusťte příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-128">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="a9d08-129">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a9d08-129">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="a9d08-130">Výchozí šablona vytvoří aplikaci, která se vytiskne do terminálu a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="a9d08-130">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="a9d08-131">V tomto kurzu použijete aplikaci, která bude mít neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-131">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="a9d08-132">V textovém editoru otevřete soubor *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-132">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="a9d08-133">V současné době by měl vypadat jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a9d08-133">It should currently look like the following code:</span></span>

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

<span data-ttu-id="a9d08-134">Nahraďte soubor následujícím kódem, který počítá čísla každou sekundu:</span><span class="sxs-lookup"><span data-stu-id="a9d08-134">Replace the file with the following code that counts numbers every second:</span></span>

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
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="a9d08-135">Uložte soubor a znovu otestujte program pomocí `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-135">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="a9d08-136">Mějte na paměti, že tato aplikace bude běžet po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-136">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="a9d08-137">Pomocí příkazu Cancel <kbd>CTRL</kbd>+<kbd>C</kbd> zastavte.</span><span class="sxs-lookup"><span data-stu-id="a9d08-137">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="a9d08-138">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a9d08-138">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="a9d08-139">Pokud předáte číslo do příkazového řádku do aplikace, bude se počítat jenom s touto velikostí a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="a9d08-139">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="a9d08-140">Zkuste to s `dotnet run -- 5`, abyste se mohli počítat na pět.</span><span class="sxs-lookup"><span data-stu-id="a9d08-140">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="a9d08-141">Jakékoli parametry po `--` nejsou předány do příkazu `dotnet run` a místo toho jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9d08-141">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="a9d08-142">Publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-142">Publish .NET Core app</span></span>

<span data-ttu-id="a9d08-143">Před přidáním aplikace .NET Core do image Docker ji publikujte.</span><span class="sxs-lookup"><span data-stu-id="a9d08-143">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="a9d08-144">Chcete se ujistit, že kontejner spouští publikovanou verzi aplikace, když je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="a9d08-144">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="a9d08-145">Z pracovní složky zadejte složku *aplikace* s příkladem zdrojového kódu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a9d08-145">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="a9d08-146">Tento příkaz zkompiluje vaši aplikaci do složky pro *publikování* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-146">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="a9d08-147">Cesta ke složce pro *publikování* z pracovní složky by měla být `.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="a9d08-147">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="a9d08-148">Ve složce *aplikace* Získejte výpis adresáře složky pro publikování a ověřte, zda byl vytvořen soubor *MyApp. dll* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-148">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span> 

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="a9d08-149">Pokud používáte Linux nebo macOS, pomocí příkazu `ls` Získejte výpis adresáře a ověřte, zda byl vytvořen soubor *MyApp. dll* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-149">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="a9d08-150">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="a9d08-150">Create the Dockerfile</span></span>

<span data-ttu-id="a9d08-151">Soubor *souboru Dockerfile* je používán příkazem `docker build` k vytvoření image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-151">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="a9d08-152">Tento soubor je textový soubor s názvem *souboru Dockerfile* , který nemá příponu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-152">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="a9d08-153">V terminálu přejděte v adresáři do pracovní složky, kterou jste vytvořili na začátku.</span><span class="sxs-lookup"><span data-stu-id="a9d08-153">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="a9d08-154">Vytvořte v pracovní složce soubor s názvem *souboru Dockerfile* a otevřete ho v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-154">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="a9d08-155">V závislosti na typu aplikace, kterou se chystáte kontejnerizace, zvolíte buď modul runtime ASP.NET Core, nebo modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-155">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="a9d08-156">V případě pochybností vyberte modul runtime ASP.NET Core, který zahrnuje modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-156">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="a9d08-157">Tento kurz použije bitovou kopii ASP.NET Core Runtime, ale aplikace vytvořená v předchozích částech je aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-157">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="a9d08-158">Modul runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9d08-158">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="a9d08-159">Modul runtime .NET core</span><span class="sxs-lookup"><span data-stu-id="a9d08-159">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="a9d08-160">Příkaz `FROM` instruuje Docker, aby vyčetl obrázek s příznakem **3,1** ze zadaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="a9d08-160">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="a9d08-161">Ujistěte se, že si vyžádáte verzi modulu runtime, která odpovídá modulu runtime, který cílí na vaši sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="a9d08-161">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="a9d08-162">Například aplikace vytvořená v předchozím oddílu používala sadu .NET Core 3,1 SDK a základní image, na kterou odkazuje *souboru Dockerfile* , jsou označené **3,1**.</span><span class="sxs-lookup"><span data-stu-id="a9d08-162">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="a9d08-163">Uložte soubor *souboru Dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="a9d08-163">Save the *Dockerfile* file.</span></span> <span data-ttu-id="a9d08-164">Adresářová struktura pracovní složky by měla vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="a9d08-164">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="a9d08-165">Některé soubory hlubší úrovně a složky byly vyjmuty, aby se ušetřilo místo v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="a9d08-165">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="a9d08-166">Z terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a9d08-166">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="a9d08-167">Docker zpracuje každý řádek v *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="a9d08-167">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="a9d08-168">`.` v příkazu `docker build` dá Docker pokyn k použití aktuální složky k vyhledání *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="a9d08-168">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="a9d08-169">Tento příkaz sestaví image a vytvoří místní úložiště s názvem **MyImage** , které odkazuje na tuto image.</span><span class="sxs-lookup"><span data-stu-id="a9d08-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="a9d08-170">Po dokončení tohoto příkazu spusťte `docker images` pro zobrazení seznamu nainstalovaných imagí:</span><span class="sxs-lookup"><span data-stu-id="a9d08-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="a9d08-171">Všimněte si, že tyto dva obrázky sdílejí stejnou hodnotu **ID obrázku** .</span><span class="sxs-lookup"><span data-stu-id="a9d08-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="a9d08-172">Tato hodnota je stejná mezi oběma obrazci, protože jediný příkaz v *souboru Dockerfile* byl založen na novém obrázku na stávající imagi.</span><span class="sxs-lookup"><span data-stu-id="a9d08-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="a9d08-173">Pojďme do *souboru Dockerfile*přidat dva příkazy.</span><span class="sxs-lookup"><span data-stu-id="a9d08-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="a9d08-174">Každý příkaz vytvoří novou vrstvu obrázku s posledním příkazem reprezentujícím obrázek, na který odkazuje položka úložiště **MyImage** .</span><span class="sxs-lookup"><span data-stu-id="a9d08-174">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="a9d08-175">Příkaz `COPY` dá Docker pokyn ke zkopírování zadané složky ve vašem počítači do složky v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="a9d08-176">V tomto příkladu je složka pro *publikování* zkopírována do složky s názvem *App* v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-176">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="a9d08-177">Následující příkaz `ENTRYPOINT`, dá Docker pokyn ke konfiguraci kontejneru tak, aby běžel jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="a9d08-177">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="a9d08-178">Po spuštění kontejneru se spustí příkaz `ENTRYPOINT`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="a9d08-179">Po ukončení tohoto příkazu se kontejner automaticky zastaví.</span><span class="sxs-lookup"><span data-stu-id="a9d08-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="a9d08-180">V terminálu spusťte `docker build -t myimage -f Dockerfile .` a po dokončení tohoto příkazu spusťte `docker images`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="a9d08-181">Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořila **ID obrázku**.</span><span class="sxs-lookup"><span data-stu-id="a9d08-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="a9d08-182">Konečné **ID image** (bude se lišit) bude **ddcc6646461b** a dál vytvoříte kontejner na základě tohoto obrázku.</span><span class="sxs-lookup"><span data-stu-id="a9d08-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="a9d08-183">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="a9d08-183">Create a container</span></span>

<span data-ttu-id="a9d08-184">Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="a9d08-185">Kontejner můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="a9d08-185">You can create a container in two ways.</span></span> <span data-ttu-id="a9d08-186">Nejdřív vytvořte nový kontejner, který se zastaví.</span><span class="sxs-lookup"><span data-stu-id="a9d08-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="a9d08-187">Výše uvedený příkaz `docker create` vytvoří kontejner založený na imagi **MyImage** .</span><span class="sxs-lookup"><span data-stu-id="a9d08-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="a9d08-188">Výstup tohoto příkazu ukazuje **ID kontejneru** (bude se lišit) vytvořeného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="a9d08-189">Chcete-li zobrazit seznam *všech* kontejnerů, použijte příkaz `docker ps -a`:</span><span class="sxs-lookup"><span data-stu-id="a9d08-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="a9d08-190">Správa kontejneru</span><span class="sxs-lookup"><span data-stu-id="a9d08-190">Manage the container</span></span>

<span data-ttu-id="a9d08-191">Každému kontejneru je přiřazen náhodný název, který můžete použít k odkazování na tuto instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="a9d08-192">Například kontejner, který byl vytvořen automaticky, zvolil název **gallant_lehmann** (vaše se bude lišit) a tento název lze použít ke spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-192">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="a9d08-193">Automatický název přepíšete pomocí parametru `docker create --name`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="a9d08-194">Následující příklad používá příkaz `docker start` ke spuštění kontejneru a poté používá příkaz `docker ps` k zobrazení pouze kontejnerů, které jsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="a9d08-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="a9d08-195">Podobně příkaz `docker stop` zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="a9d08-196">Následující příklad používá příkaz `docker stop` pro zastavení kontejneru a poté pomocí příkazu `docker ps` zobrazí, že žádné kontejnery nejsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="a9d08-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="a9d08-197">Připojit ke kontejneru</span><span class="sxs-lookup"><span data-stu-id="a9d08-197">Connect to a container</span></span>

<span data-ttu-id="a9d08-198">Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="a9d08-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="a9d08-199">Použijte příkazy `docker start` a `docker attach` ke spuštění kontejneru a k prohlížení výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="a9d08-200">V tomto příkladu se k odpojení od běžícího kontejneru používá <kbd>Klávesová zkratka CTRL + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="a9d08-200">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="a9d08-201">Tento klávesová zkratka může ve skutečnosti ukončit proces v kontejneru, čímž se kontejner zastaví.</span><span class="sxs-lookup"><span data-stu-id="a9d08-201">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="a9d08-202">Parametr `--sig-proxy=false` zajišťuje, že <kbd>CTRL + C</kbd> nezastaví proces v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="a9d08-203">Po odpojení od kontejneru znovu připojte, abyste ověřili, že pořád běží a počítá se.</span><span class="sxs-lookup"><span data-stu-id="a9d08-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="a9d08-204">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="a9d08-204">Delete a container</span></span>

<span data-ttu-id="a9d08-205">Pro účely tohoto článku nechcete, aby kontejnery právě neprováděly žádné akce.</span><span class="sxs-lookup"><span data-stu-id="a9d08-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="a9d08-206">Odstraňte kontejner, který jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="a9d08-206">Delete the container you previously created.</span></span> <span data-ttu-id="a9d08-207">Pokud je kontejner spuštěný, zastavte ho.</span><span class="sxs-lookup"><span data-stu-id="a9d08-207">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="a9d08-208">Následující příklad zobrazí seznam všech kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="a9d08-208">The following example lists all containers.</span></span> <span data-ttu-id="a9d08-209">Pak pomocí příkazu `docker rm` odstraní kontejner a pak u všech spuštěných kontejnerů zkontroluje druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="a9d08-210">Jeden běh</span><span class="sxs-lookup"><span data-stu-id="a9d08-210">Single run</span></span>

<span data-ttu-id="a9d08-211">Docker poskytuje příkaz `docker run` pro vytvoření a spuštění kontejneru jako jediného příkazu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="a9d08-212">Tento příkaz eliminuje nutnost spuštění `docker create` a pak `docker start`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="a9d08-213">Tento příkaz lze také nastavit tak, aby při zastavení kontejneru automaticky odstranil kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="a9d08-214">Například použijte `docker run -it --rm` k provedení dvou věcí, nejprve automatické použití aktuálního terminálu pro připojení ke kontejneru a po dokončení kontejneru odeberte:</span><span class="sxs-lookup"><span data-stu-id="a9d08-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="a9d08-215">V `docker run -it`příkaz <kbd>CTRL + C</kbd> zastaví proces, který je spuštěný v kontejneru, který zase zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="a9d08-216">Vzhledem k tomu, že byl zadán parametr `--rm`, kontejner je automaticky odstraněn při zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="a9d08-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="a9d08-217">Ověřte, že neexistuje:</span><span class="sxs-lookup"><span data-stu-id="a9d08-217">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="a9d08-218">Změnit vstupní bod</span><span class="sxs-lookup"><span data-stu-id="a9d08-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="a9d08-219">Příkaz `docker run` také umožňuje upravit `ENTRYPOINT` příkaz z *souboru Dockerfile* a spustit něco jiného, ale pouze pro tento kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="a9d08-220">Například pomocí následujícího příkazu spusťte `bash` nebo `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="a9d08-221">V případě potřeby upravte příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9d08-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="a9d08-222">Windows</span><span class="sxs-lookup"><span data-stu-id="a9d08-222">Windows</span></span>

<span data-ttu-id="a9d08-223">V tomto příkladu se `ENTRYPOINT` změní na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="a9d08-224">Stiskem <kbd>klávesy CTRL</kbd>+<kbd>C</kbd> ukončíte proces a zastavíte kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-224"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="a9d08-225">Linux</span><span class="sxs-lookup"><span data-stu-id="a9d08-225">Linux</span></span>

<span data-ttu-id="a9d08-226">V tomto příkladu se `ENTRYPOINT` změní na `bash`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="a9d08-227">Spustí se příkaz `quit`, který ukončí proces a zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="a9d08-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="a9d08-228">Důležité příkazy</span><span class="sxs-lookup"><span data-stu-id="a9d08-228">Essential commands</span></span>

<span data-ttu-id="a9d08-229">Docker má mnoho různých příkazů, které pokrývají, co chcete s kontejnerem a obrázky udělat.</span><span class="sxs-lookup"><span data-stu-id="a9d08-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="a9d08-230">Tyto příkazy Docker jsou zásadní pro správu vašich kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="a9d08-230">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="a9d08-231">sestavení Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="a9d08-232">spuštění Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="a9d08-233">Docker PS</span><span class="sxs-lookup"><span data-stu-id="a9d08-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="a9d08-234">zastavení Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="a9d08-235">Docker RM</span><span class="sxs-lookup"><span data-stu-id="a9d08-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="a9d08-236">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="a9d08-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="a9d08-237">Obrázek Docker</span><span class="sxs-lookup"><span data-stu-id="a9d08-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="a9d08-238">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="a9d08-238">Clean up resources</span></span>

<span data-ttu-id="a9d08-239">Během tohoto kurzu jste vytvořili kontejnery a image.</span><span class="sxs-lookup"><span data-stu-id="a9d08-239">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="a9d08-240">Pokud chcete, tyto prostředky odstraňte.</span><span class="sxs-lookup"><span data-stu-id="a9d08-240">If you want, delete these resources.</span></span> <span data-ttu-id="a9d08-241">Následující příkazy použijte k</span><span class="sxs-lookup"><span data-stu-id="a9d08-241">Use the following commands to</span></span>

01. <span data-ttu-id="a9d08-242">Vypsat všechny kontejnery</span><span class="sxs-lookup"><span data-stu-id="a9d08-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="a9d08-243">Zastavte kontejnery, které jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="a9d08-243">Stop containers that are running.</span></span> <span data-ttu-id="a9d08-244">`CONTAINER_NAME` představuje název automaticky přiřazený kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d08-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="a9d08-245">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="a9d08-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="a9d08-246">Pak na počítači odstraňte všechny image, které už nechcete.</span><span class="sxs-lookup"><span data-stu-id="a9d08-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="a9d08-247">Odstraňte image vytvořenou *souboru Dockerfile* a pak odstraňte image .NET Core, na které byl *souboru Dockerfile* založen.</span><span class="sxs-lookup"><span data-stu-id="a9d08-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="a9d08-248">Můžete použít **ID obrázku** nebo **úložiště:** řetězec ve formátu značek.</span><span class="sxs-lookup"><span data-stu-id="a9d08-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="a9d08-249">K zobrazení seznamu nainstalovaných imagí použijte příkaz `docker images`.</span><span class="sxs-lookup"><span data-stu-id="a9d08-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="a9d08-250">Soubory obrázků můžou být velké.</span><span class="sxs-lookup"><span data-stu-id="a9d08-250">Image files can be large.</span></span> <span data-ttu-id="a9d08-251">Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9d08-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="a9d08-252">Při plánování vytváření dalších imagí na základě tohoto modulu runtime obvykle zachováte základní image s nainstalovaným modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="a9d08-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a9d08-253">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a9d08-253">Next steps</span></span>

- [<span data-ttu-id="a9d08-254">Naučte se, jak kontejnerizace aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9d08-254">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="a9d08-255">Vyzkoušejte si kurz ASP.NET Core mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="a9d08-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="a9d08-256">Projděte si služby Azure, které podporují kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a9d08-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="a9d08-257">Přečtěte si o příkazech souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a9d08-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="a9d08-258">Prozkoumejte nástroje kontejnerů pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9d08-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
