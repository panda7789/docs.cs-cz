---
title: Kontejnerize aplikace s kurzem Dockeru
description: V tomto kurzu se dozvíte, jak kontejnerizovat aplikaci .NET Core s Dockerem.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546572"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="c7142-103">Kurz: Kontejnerize aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7142-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="c7142-104">Tento kurz vás naučí, jak vytvořit bitovou kopii Dockeru, která obsahuje vaši aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7142-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="c7142-105">Image lze použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="c7142-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="c7142-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="c7142-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c7142-107">Vytvoření a publikování jednoduché aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7142-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="c7142-108">Vytvoření a konfigurace souboru Dockerfile pro jádro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c7142-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="c7142-109">Sestavení image Dockeru</span><span class="sxs-lookup"><span data-stu-id="c7142-109">Build a Docker image</span></span>
> - <span data-ttu-id="c7142-110">Vytvoření a spuštění kontejneru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c7142-110">Create and run a Docker container</span></span>

<span data-ttu-id="c7142-111">Porozumíte sestavení a nasazení úloh kontejneru Dockeru pro aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7142-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="c7142-112">*Platforma Dockeru* používá *modul Dockeru* k rychlému vytváření a balení aplikací jako *imitace Dockeru*.</span><span class="sxs-lookup"><span data-stu-id="c7142-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="c7142-113">Tyto image jsou zapsány ve formátu *Dockerfile* k nasazení a spuštění ve vrstvené kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!WARNING]
> <span data-ttu-id="c7142-114">**Tento kurz není pro aplikace ASP.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="c7142-114">**This tutorial isn't for ASP.NET Core apps.**</span></span> <span data-ttu-id="c7142-115">Pokud používáte ASP.NET Core, přečtěte [si naučte se, jak kontejnerizovat ASP.NET základní aplikace](/aspnet/core/host-and-deploy/docker/building-net-docker-images) kurzu.</span><span class="sxs-lookup"><span data-stu-id="c7142-115">If you're using ASP.NET Core, read the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7142-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7142-116">Prerequisites</span></span>

<span data-ttu-id="c7142-117">Nainstalujte následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="c7142-117">Install the following prerequisites:</span></span>

- <span data-ttu-id="c7142-118">[Sada SDK jádra .NET 3.1](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="c7142-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="c7142-119">Pokud máte nainstalovanou službu `dotnet --info` .NET Core, použijte příkaz k určení, kterou sadu SDK používáte.</span><span class="sxs-lookup"><span data-stu-id="c7142-119">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="c7142-120">Komunitní edice Dockeru</span><span class="sxs-lookup"><span data-stu-id="c7142-120">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="c7142-121">Dočasná pracovní složka pro *aplikaci Dockerfile* a .NET Core example.</span><span class="sxs-lookup"><span data-stu-id="c7142-121">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="c7142-122">V tomto kurzu název *docker-working* se používá jako pracovní složka.</span><span class="sxs-lookup"><span data-stu-id="c7142-122">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="c7142-123">Vytvoření aplikace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7142-123">Create .NET Core app</span></span>

<span data-ttu-id="c7142-124">Potřebujete aplikaci .NET Core, kterou spustí kontejner Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c7142-124">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="c7142-125">Otevřete terminál, vytvořte pracovní složku, pokud jste tak dosud neučinili, a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="c7142-125">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="c7142-126">V pracovní složce spusťte následující příkaz a vytvořte nový projekt v podadresáři s názvem *app*:</span><span class="sxs-lookup"><span data-stu-id="c7142-126">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="c7142-127">Strom složek bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="c7142-127">Your folder tree will look like the following:</span></span>

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

<span data-ttu-id="c7142-128">Příkaz `dotnet new` vytvoří novou složku s názvem *aplikace* a generuje aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c7142-128">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="c7142-129">Zadejte složku *aplikace* a `dotnet run`spusťte příkaz .</span><span class="sxs-lookup"><span data-stu-id="c7142-129">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="c7142-130">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c7142-130">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="c7142-131">Výchozí šablona vytvoří aplikaci, která se vytiskne na terminál a poté ji ukončí.</span><span class="sxs-lookup"><span data-stu-id="c7142-131">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="c7142-132">Pro účely tohoto kurzu budete používat aplikaci, která smyčky neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="c7142-132">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="c7142-133">Otevřete *soubor Program.cs* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="c7142-133">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="c7142-134">V současné době by měl vypadat jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="c7142-134">It should currently look like the following code:</span></span>

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

<span data-ttu-id="c7142-135">Nahraďte soubor následujícím kódem, který počítá čísla každou sekundu:</span><span class="sxs-lookup"><span data-stu-id="c7142-135">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="c7142-136">Uložte soubor a otestujte program znovu pomocí aplikace `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="c7142-136">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="c7142-137">Nezapomeňte, že tato aplikace běží neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="c7142-137">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="c7142-138">Chcete-li příkaz cancel <kbd>CTRL</kbd>+<kbd>C,</kbd> zastavte jej.</span><span class="sxs-lookup"><span data-stu-id="c7142-138">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="c7142-139">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c7142-139">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="c7142-140">Pokud aplikaci předáte číslo na příkazovém řádku, bude se počítat pouze do této částky a pak ji ukončíte.</span><span class="sxs-lookup"><span data-stu-id="c7142-140">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="c7142-141">Zkus to `dotnet run -- 5` s počítat do pěti.</span><span class="sxs-lookup"><span data-stu-id="c7142-141">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="c7142-142">Všechny parametry `--` po nejsou `dotnet run` předány příkazu a místo toho jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7142-142">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="c7142-143">Publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7142-143">Publish .NET Core app</span></span>

<span data-ttu-id="c7142-144">Než přidáte aplikaci .NET Core do bitové kopie Dockeru, publikujte ji.</span><span class="sxs-lookup"><span data-stu-id="c7142-144">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="c7142-145">Chcete se ujistit, že kontejner spustí publikovanou verzi aplikace při spuštění.</span><span class="sxs-lookup"><span data-stu-id="c7142-145">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="c7142-146">Z pracovní složky zadejte složku *aplikace* s ukázkovým zdrojovým kódem a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7142-146">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="c7142-147">Tento příkaz zkompiluje aplikaci do složky *publikování.*</span><span class="sxs-lookup"><span data-stu-id="c7142-147">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="c7142-148">Cesta ke složce *publikování* z pracovní složky by měla být`.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="c7142-148">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="c7142-149">Ze složky *aplikace* získáte seznam adresářů složky publikování, abyste ověřili, že byl vytvořen soubor *myapp.dll.*</span><span class="sxs-lookup"><span data-stu-id="c7142-149">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

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

<span data-ttu-id="c7142-150">Pokud používáte Linux nebo macOS, `ls` pomocí příkazu získejte výpis adresáře a ověřte, zda byl vytvořen soubor *myapp.dll.*</span><span class="sxs-lookup"><span data-stu-id="c7142-150">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="c7142-151">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="c7142-151">Create the Dockerfile</span></span>

<span data-ttu-id="c7142-152">Soubor *Dockerfile* se používá `docker build` příkazem k vytvoření image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-152">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="c7142-153">Tento soubor je textový soubor s názvem *Dockerfile,* který nemá příponu.</span><span class="sxs-lookup"><span data-stu-id="c7142-153">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="c7142-154">V terminálu přejděte do adresáře do pracovní složky, kterou jste vytvořili na začátku.</span><span class="sxs-lookup"><span data-stu-id="c7142-154">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="c7142-155">Vytvořte soubor s názvem *Dockerfile* v pracovní složce a otevřete jej v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="c7142-155">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="c7142-156">V závislosti na typu aplikace, kterou chcete kontejnerizovat, zvolíte buď ASP.NET core runtime nebo .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="c7142-156">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="c7142-157">Pokud jste na pochybách, zvolte ASP.NET core runtime, který zahrnuje .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="c7142-157">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="c7142-158">Tento kurz bude používat ASP.NET image core runtime, ale aplikace vytvořená v předchozích částech je aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7142-158">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="c7142-159">ASP.NET core runtime</span><span class="sxs-lookup"><span data-stu-id="c7142-159">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="c7142-160">Doba běhu jádra .NET</span><span class="sxs-lookup"><span data-stu-id="c7142-160">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="c7142-161">Příkaz `FROM` říká Dockeru, aby stáhl obrázek označený **3.1** ze zadaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="c7142-161">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="c7142-162">Ujistěte se, že vytáhnete runtime verzi, která odpovídá runtime cílené sdk.</span><span class="sxs-lookup"><span data-stu-id="c7142-162">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="c7142-163">Například aplikace vytvořená v předchozí části používala sdk rozhraní .NET Core 3.1 a základní bitovou kopii uvedenou v *souboru Dockerfile* je označena **hodnotou 3.1**.</span><span class="sxs-lookup"><span data-stu-id="c7142-163">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="c7142-164">Uložte soubor *Dockerfile.*</span><span class="sxs-lookup"><span data-stu-id="c7142-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="c7142-165">Adresářová struktura pracovní složky by měla vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="c7142-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="c7142-166">Některé soubory a složky na hlubší úrovni byly v článku vyříznuty, aby se ušetřilo místo:</span><span class="sxs-lookup"><span data-stu-id="c7142-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

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

<span data-ttu-id="c7142-167">Z terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7142-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="c7142-168">Docker zpracuje každý řádek v *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c7142-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="c7142-169">Příkaz `.` v `docker build` příkazu říká Dockeru, aby použil aktuální složku k nalezení *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c7142-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="c7142-170">Tento příkaz vytvoří image a vytvoří místní úložiště s názvem **myimage,** který odkazuje na tuto bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c7142-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="c7142-171">Po dokončení tohoto příkazu se spusťte `docker images` a zobrazte seznam nainstalovaných bitových kopií:</span><span class="sxs-lookup"><span data-stu-id="c7142-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="c7142-172">Všimněte si, že dva obrazy sdílejí stejnou hodnotu **ID image.**</span><span class="sxs-lookup"><span data-stu-id="c7142-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="c7142-173">Hodnota je stejná mezi oběma bitovými kopiemi, protože jediným příkazem v *souboru Dockerfile* bylo založit novou bitovou kopii na existující bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="c7142-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="c7142-174">Přidáme dva příkazy do *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c7142-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="c7142-175">Každý příkaz vytvoří novou vrstvu obrazu s konečným příkazem představujícím obraz, na který položka úložiště **myimage** odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c7142-175">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="c7142-176">Příkaz `COPY` říká Dockeru, aby zkopíroval zadanou složku v počítači do složky v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="c7142-177">V tomto příkladu se složka *publikování* zkopíruje do složky s názvem *aplikace* v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="c7142-178">Další příkaz `ENTRYPOINT`, říká Docker nakonfigurovat kontejner spustit jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c7142-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="c7142-179">Při spuštění kontejneru `ENTRYPOINT` se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="c7142-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="c7142-180">Když tento příkaz skončí, kontejner se automaticky zastaví.</span><span class="sxs-lookup"><span data-stu-id="c7142-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="c7142-181">Z terminálu, `docker build -t myimage -f Dockerfile .` spustit a po dokončení `docker images`tohoto příkazu, spustit .</span><span class="sxs-lookup"><span data-stu-id="c7142-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

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

<span data-ttu-id="c7142-182">Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořil **ID IMAGE**.</span><span class="sxs-lookup"><span data-stu-id="c7142-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="c7142-183">Konečné **ID image** (vaše bude jiné) je **ddcc6646461b** a dále vytvoříte kontejner založený na tomto obrázku.</span><span class="sxs-lookup"><span data-stu-id="c7142-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="c7142-184">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="c7142-184">Create a container</span></span>

<span data-ttu-id="c7142-185">Teď, když máte obrázek, který obsahuje vaši aplikaci, můžete vytvořit kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="c7142-186">Kontejner můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="c7142-186">You can create a container in two ways.</span></span> <span data-ttu-id="c7142-187">Nejprve vytvořte nový kontejner, který je zastaven.</span><span class="sxs-lookup"><span data-stu-id="c7142-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="c7142-188">Příkaz `docker create` shora vytvoří kontejner založený na image **myimage.**</span><span class="sxs-lookup"><span data-stu-id="c7142-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="c7142-189">Výstup tohoto příkazu zobrazí **ID kontejneru** (vaše se bude lišit) vytvořeného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="c7142-190">Chcete-li zobrazit seznam *všech* `docker ps -a` kontejnerů, použijte příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7142-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="c7142-191">Správa kontejneru</span><span class="sxs-lookup"><span data-stu-id="c7142-191">Manage the container</span></span>

<span data-ttu-id="c7142-192">Každému kontejneru je přiřazen náhodný název, který můžete použít k odkazování na tuto instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="c7142-193">Například kontejner, který byl vytvořen automaticky vybral název **gallant_lehmann** (vaše se bude lišit) a tento název lze použít ke spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-193">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="c7142-194">Automatický název přepíšete určitým názvem pomocí `docker create --name` parametru.</span><span class="sxs-lookup"><span data-stu-id="c7142-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="c7142-195">Následující příklad používá `docker start` příkaz ke spuštění kontejneru `docker ps` a potom používá příkaz zobrazit pouze kontejnery, které jsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="c7142-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="c7142-196">Podobně `docker stop` příkaz zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="c7142-197">Následující příklad používá `docker stop` příkaz k zastavení kontejneru `docker ps` a potom pomocí příkazu zobrazí, že jsou spuštěny žádné kontejnery:</span><span class="sxs-lookup"><span data-stu-id="c7142-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="c7142-198">Připojení ke kontejneru</span><span class="sxs-lookup"><span data-stu-id="c7142-198">Connect to a container</span></span>

<span data-ttu-id="c7142-199">Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="c7142-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="c7142-200">Pomocí `docker start` příkazů `docker attach` a spusťte kontejner a prohlédněte si výstupní datový proud.</span><span class="sxs-lookup"><span data-stu-id="c7142-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="c7142-201">V tomto příkladu <kbd>klávesy CTRL + C</kbd> se používá k odpojení od spuštěného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-201">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="c7142-202">Tento úhoz může ve skutečnosti ukončit proces v kontejneru, který zastaví kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-202">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="c7142-203">Parametr `--sig-proxy=false` zajišťuje, že <kbd>CTRL + C</kbd> nezastaví proces v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="c7142-204">Po odpojení od kontejneru znovu připojte a ověřte, zda je stále spuštěna a počítá.</span><span class="sxs-lookup"><span data-stu-id="c7142-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="c7142-205">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="c7142-205">Delete a container</span></span>

<span data-ttu-id="c7142-206">Pro účely tohoto článku nechcete, aby kontejnery jen poflakovat nic nedělá.</span><span class="sxs-lookup"><span data-stu-id="c7142-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="c7142-207">Odstraňte kontejner, který jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="c7142-207">Delete the container you previously created.</span></span> <span data-ttu-id="c7142-208">Pokud je kontejner spuštěn, zastavte jej.</span><span class="sxs-lookup"><span data-stu-id="c7142-208">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="c7142-209">V následujícím příkladu jsou uvedeny všechny kontejnery.</span><span class="sxs-lookup"><span data-stu-id="c7142-209">The following example lists all containers.</span></span> <span data-ttu-id="c7142-210">Potom pomocí `docker rm` příkazu odstranit kontejner a potom zkontroluje podruhé pro všechny spuštěné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="c7142-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="c7142-211">Jeden běh</span><span class="sxs-lookup"><span data-stu-id="c7142-211">Single run</span></span>

<span data-ttu-id="c7142-212">Docker poskytuje `docker run` příkaz k vytvoření a spuštění kontejneru jako jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="c7142-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="c7142-213">Tento příkaz eliminuje potřebu `docker create` spuštění `docker start`a potom .</span><span class="sxs-lookup"><span data-stu-id="c7142-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="c7142-214">Tento příkaz můžete také nastavit tak, aby automaticky odstranil kontejner, když se kontejner zastaví.</span><span class="sxs-lookup"><span data-stu-id="c7142-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="c7142-215">Například použijte `docker run -it --rm` k provedení dvou věcí, nejprve automaticky použijte aktuální terminál pro připojení ke kontejneru a po dokončení kontejneru jej odeberte:</span><span class="sxs-lookup"><span data-stu-id="c7142-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="c7142-216">Pomocí `docker run -it`příkazu <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, což zase zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="c7142-217">Vzhledem `--rm` k tomu, že parametr byl poskytnut, kontejner je automaticky odstraněn při zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="c7142-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="c7142-218">Ověřte, zda neexistuje:</span><span class="sxs-lookup"><span data-stu-id="c7142-218">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="c7142-219">Změna vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="c7142-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="c7142-220">Příkaz `docker run` také umožňuje upravit `ENTRYPOINT` příkaz z *Dockerfile* a spustit něco jiného, ale pouze pro tento kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="c7142-221">Pomocí následujícího příkazu můžete `bash` `cmd.exe`například spustit nebo .</span><span class="sxs-lookup"><span data-stu-id="c7142-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="c7142-222">Podle potřeby upravte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c7142-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="c7142-223">Windows</span><span class="sxs-lookup"><span data-stu-id="c7142-223">Windows</span></span>

<span data-ttu-id="c7142-224">V tomto `ENTRYPOINT` příkladu `cmd.exe`se změní na .</span><span class="sxs-lookup"><span data-stu-id="c7142-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="c7142-225"><kbd>Ctrl</kbd>+<kbd>C</kbd> je stisknuto ukončit proces a zastavit kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-225"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="c7142-226">Linux</span><span class="sxs-lookup"><span data-stu-id="c7142-226">Linux</span></span>

<span data-ttu-id="c7142-227">V tomto `ENTRYPOINT` příkladu `bash`se změní na .</span><span class="sxs-lookup"><span data-stu-id="c7142-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="c7142-228">Příkaz `quit` je spuštěn, který ukončí proces a zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="c7142-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="c7142-229">Základní příkazy</span><span class="sxs-lookup"><span data-stu-id="c7142-229">Essential commands</span></span>

<span data-ttu-id="c7142-230">Docker má mnoho různých příkazů, které pokrývají, co chcete dělat s kontejnerem a image.</span><span class="sxs-lookup"><span data-stu-id="c7142-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="c7142-231">Tyto příkazy Dockeru jsou nezbytné pro správu kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="c7142-231">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="c7142-232">docker build</span><span class="sxs-lookup"><span data-stu-id="c7142-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="c7142-233">docker spustit</span><span class="sxs-lookup"><span data-stu-id="c7142-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="c7142-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="c7142-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="c7142-235">docker stop</span><span class="sxs-lookup"><span data-stu-id="c7142-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="c7142-236">docker rm</span><span class="sxs-lookup"><span data-stu-id="c7142-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="c7142-237">docker rmi</span><span class="sxs-lookup"><span data-stu-id="c7142-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="c7142-238">obrázek dockeru</span><span class="sxs-lookup"><span data-stu-id="c7142-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="c7142-239">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="c7142-239">Clean up resources</span></span>

<span data-ttu-id="c7142-240">Během tohoto kurzu jste vytvořili kontejnery a obrázky.</span><span class="sxs-lookup"><span data-stu-id="c7142-240">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="c7142-241">Pokud chcete, odstraňte tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="c7142-241">If you want, delete these resources.</span></span> <span data-ttu-id="c7142-242">Pomocí následujících příkazů</span><span class="sxs-lookup"><span data-stu-id="c7142-242">Use the following commands to</span></span>

01. <span data-ttu-id="c7142-243">Vypsat všechny kontejnery</span><span class="sxs-lookup"><span data-stu-id="c7142-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="c7142-244">Zastavit kontejnery, které jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="c7142-244">Stop containers that are running.</span></span> <span data-ttu-id="c7142-245">Představuje `CONTAINER_NAME` název automaticky přiřazený kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c7142-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="c7142-246">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="c7142-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="c7142-247">Dále odstraňte všechny obrázky, které již v počítači nechcete.</span><span class="sxs-lookup"><span data-stu-id="c7142-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="c7142-248">Odstraňte bitovou kopii vytvořenou *souborem Dockerfile* a potom odstraňte bitovou kopii .NET Core, na které byl soubor *Dockerfile* založen.</span><span class="sxs-lookup"><span data-stu-id="c7142-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="c7142-249">Můžete použít **ID OBRAZU** nebo řetězec ve formátu **REPOSITORY:TAG.**</span><span class="sxs-lookup"><span data-stu-id="c7142-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="c7142-250">Pomocí `docker images` příkazu zobrazíte seznam nainstalovaných bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="c7142-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="c7142-251">Obrazové soubory mohou být velké.</span><span class="sxs-lookup"><span data-stu-id="c7142-251">Image files can be large.</span></span> <span data-ttu-id="c7142-252">Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7142-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="c7142-253">Obvykle uchováváte základní bitové kopie s nainstalovaným runtime, pokud plánujete vytvářet další bitové kopie na základě tohoto běhu.</span><span class="sxs-lookup"><span data-stu-id="c7142-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7142-254">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c7142-254">Next steps</span></span>

- [<span data-ttu-id="c7142-255">Přečtěte si, jak kontejnerizovat aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7142-255">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="c7142-256">Vyzkoušejte kurz ASP.NET Core Microservice.</span><span class="sxs-lookup"><span data-stu-id="c7142-256">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="c7142-257">Zkontrolujte služby Azure, které podporují kontejnery.</span><span class="sxs-lookup"><span data-stu-id="c7142-257">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="c7142-258">Přečtěte si o příkazech Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c7142-258">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="c7142-259">Prozkoumejte nástroje kontejneru pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7142-259">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
