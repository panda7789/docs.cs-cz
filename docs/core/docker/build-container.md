---
title: Kontejnerizace aplikace pomocí Docker kurz
description: V tomto kurzu se dozvíte, jak kontejnerizovat aplikace .NET Core s Dockerem.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: cb9a53520c513d96b9b1656ad64d55cf8aea1f08
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870429"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="090d9-103">Kurz: Kontejnerizace aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="090d9-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="090d9-104">V tomto kurzu se naučíte, jak sestavit image Dockeru obsahující aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="090d9-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="090d9-105">Na obrázku slouží k vytvoření kontejnerů pro vaše místní vývojové prostředí, privátního cloudu nebo veřejného cloudu.</span><span class="sxs-lookup"><span data-stu-id="090d9-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="090d9-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="090d9-106">You'll learn to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="090d9-107">Vytvoření a publikování jednoduchou aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="090d9-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="090d9-108">Vytvoření a konfigurace souboru Dockerfile pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="090d9-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="090d9-109">Sestavíte image Dockeru</span><span class="sxs-lookup"><span data-stu-id="090d9-109">Build a Docker image</span></span>
> * <span data-ttu-id="090d9-110">Vytvoření a spuštění kontejneru Dockeru</span><span class="sxs-lookup"><span data-stu-id="090d9-110">Create and run a Docker container</span></span>

<span data-ttu-id="090d9-111">Rozumíte budete Docker, kontejner sestavení a nasazení úlohy pro aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="090d9-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="090d9-112">*Platforma Docker* používá *modul Docker* k rychlému sestavování a balíčky aplikací jako *imagí Dockeru*.</span><span class="sxs-lookup"><span data-stu-id="090d9-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="090d9-113">Tyto Image jsou napsané v *soubor Dockerfile* formát nasazení a spuštění v kontejneru vrstvami.</span><span class="sxs-lookup"><span data-stu-id="090d9-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="090d9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="090d9-114">Prerequisites</span></span>

<span data-ttu-id="090d9-115">Nainstalujte následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="090d9-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="090d9-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="090d9-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="090d9-117">Pokud máte nainstalovaný .NET Core, použijte `dotnet --info` příkaz k určení SDK, které používáte.</span><span class="sxs-lookup"><span data-stu-id="090d9-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="090d9-118">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="090d9-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="090d9-119">Dočasnou pracovní složku pro *soubor Dockerfile* a ukázkovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="090d9-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="090d9-120">V tomto kurzu se název `docker-working` slouží jako pracovní složku.</span><span class="sxs-lookup"><span data-stu-id="090d9-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="090d9-121">Použití sady SDK verze 2.2</span><span class="sxs-lookup"><span data-stu-id="090d9-121">Use SDK version 2.2</span></span>

<span data-ttu-id="090d9-122">Pokud používáte sadu SDK, která je novější, jako je 3.0, ujistěte se, že, že vaše aplikace bude muset používat sady SDK 2.2.</span><span class="sxs-lookup"><span data-stu-id="090d9-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="090d9-123">Vytvořte soubor s názvem `global.json` v pracovní složce a vložte následující kód json:</span><span class="sxs-lookup"><span data-stu-id="090d9-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="090d9-124">Soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="090d9-124">Save this file.</span></span> <span data-ttu-id="090d9-125">Vynutí přítomnost souboru .NET Core na použití pro všechny verze 2.2 `dotnet` příkaz volat z této složky a nižší.</span><span class="sxs-lookup"><span data-stu-id="090d9-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="090d9-126">Vytvoření .NET Core aplikace</span><span class="sxs-lookup"><span data-stu-id="090d9-126">Create .NET Core app</span></span>

<span data-ttu-id="090d9-127">Je nutné aplikaci .NET Core, který se spustí kontejner Dockeru.</span><span class="sxs-lookup"><span data-stu-id="090d9-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="090d9-128">Otevřete terminál, vytvořte pracovní složky, pokud jste to ještě neudělali a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="090d9-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="090d9-129">V pracovní složce spusťte následující příkaz pro vytvoření nového projektu v podadresáři s názvem aplikace:</span><span class="sxs-lookup"><span data-stu-id="090d9-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```console
dotnet new console -o app -n myapp
```

<span data-ttu-id="090d9-130">Strom složek bude vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="090d9-130">Your folder tree will look like the following:</span></span>

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

<span data-ttu-id="090d9-131">`dotnet new` Příkaz vytvoří novou složku s názvem *aplikace* a vygeneruje aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="090d9-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="090d9-132">Zadejte *aplikace* složky a spusťte tento příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="090d9-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="090d9-133">Se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="090d9-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="090d9-134">Výchozí šablona vytvoří aplikaci, která vytiskne do terminálu a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="090d9-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="090d9-135">Pro účely tohoto kurzu budete používat aplikaci, která smyčky po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="090d9-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="090d9-136">Otevřít **Program.cs** souboru v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="090d9-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="090d9-137">By měl nyní vypadat jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="090d9-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="090d9-138">Soubor nahraďte následující kód, který počítá každou sekundu:</span><span class="sxs-lookup"><span data-stu-id="090d9-138">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="090d9-139">Uložte soubor a testovat program znovu s `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="090d9-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="090d9-140">Mějte na paměti, že tato aplikace běží po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="090d9-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="090d9-141">Použití příkazu Storno <kbd>CTRL + C</kbd> zastavte ji.</span><span class="sxs-lookup"><span data-stu-id="090d9-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="090d9-142">Se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="090d9-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="090d9-143">Pokud předáte číslo na příkazovém řádku do aplikace, bude se pouze počítat až, který částka a poté ukončete.</span><span class="sxs-lookup"><span data-stu-id="090d9-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="090d9-144">Vyzkoušejte si to s `dotnet run -- 5` počet na 5.</span><span class="sxs-lookup"><span data-stu-id="090d9-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="090d9-145">Žádné parametry po `--` nejsou předán `dotnet run` příkazů a místo toho jsou předány do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="090d9-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="090d9-146">Publikování .NET Core aplikace</span><span class="sxs-lookup"><span data-stu-id="090d9-146">Publish .NET Core app</span></span>

<span data-ttu-id="090d9-147">Abyste mohli přidat aplikaci .NET Core do image Dockeru, publikujte ho.</span><span class="sxs-lookup"><span data-stu-id="090d9-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="090d9-148">Chcete, aby se zajistilo, že se kontejner spustí publikovanou verzi aplikace při spuštění.</span><span class="sxs-lookup"><span data-stu-id="090d9-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="090d9-149">Z pracovní složky, zadejte **aplikace** složku s příkladem zdrojového kódu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="090d9-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```console
dotnet publish -c Release
```

<span data-ttu-id="090d9-150">Tento příkaz zkompiluje aplikaci tak, aby **publikovat** složky.</span><span class="sxs-lookup"><span data-stu-id="090d9-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="090d9-151">Cesta k **publikovat** by měla být složka z pracovní složky `.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="090d9-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="090d9-152">Získat výpis složky publikování a ověřte, zda **myapp.dll** byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="090d9-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="090d9-153">Z **aplikace** složky, spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="090d9-153">From the **app** folder, run one of the following commands:</span></span>

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

## <a name="create-the-dockerfile"></a><span data-ttu-id="090d9-154">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="090d9-154">Create the Dockerfile</span></span>

<span data-ttu-id="090d9-155">*Soubor Dockerfile* soubor je používán `docker build` příkaz pro vytvoření image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="090d9-156">Tento soubor je soubor ve formátu prostého textu s názvem *soubor Dockerfile* , který nemá žádné rozšíření.</span><span class="sxs-lookup"><span data-stu-id="090d9-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="090d9-157">V terminálu přejděte na adresář pro pracovní složky, kterou jste vytvořili na začátku nahoru.</span><span class="sxs-lookup"><span data-stu-id="090d9-157">In your terminal, navigate to up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="090d9-158">Vytvořte soubor s názvem *soubor Dockerfile* ve své pracovní složce a otevřete ho v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="090d9-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="090d9-159">Jako první řádek souboru přidejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="090d9-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="090d9-160">`FROM` Příkaz říká Dockeru stáhnout image označit **2.2** z **mcr.microsoft.com/dotnet/core/runtime** úložiště.</span><span class="sxs-lookup"><span data-stu-id="090d9-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="090d9-161">Ujistěte se, že o přijetí změn na .NET Core runtime, který se shoduje s cílem sady SDK modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="090d9-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="090d9-162">Například aplikace vytvořené v předchozí části používá .NET Core 2.2 SDK a vytvořili aplikaci, na který .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="090d9-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="090d9-163">Takže základní image podle *soubor Dockerfile* je označené **2.2**.</span><span class="sxs-lookup"><span data-stu-id="090d9-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="090d9-164">Uložit *soubor Dockerfile* souboru.</span><span class="sxs-lookup"><span data-stu-id="090d9-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="090d9-165">Struktura adresářů pracovní složky by měl vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="090d9-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="090d9-166">Některé z hlubší úrovně soubory a složky byly snížili pro úsporu místa v následujícím článku:</span><span class="sxs-lookup"><span data-stu-id="090d9-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

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

<span data-ttu-id="090d9-167">Z terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="090d9-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="090d9-168">Docker bude zpracovávat každý řádek v *soubor Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="090d9-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="090d9-169">`.` v `docker build` příkaz říká Dockeru použití aktuální složku k vyhledání *soubor Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="090d9-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="090d9-170">Tento příkaz sestaví image a vytvoří místní úložiště s názvem **myimage** , která odkazuje na této bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="090d9-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="090d9-171">Po dokončení tohoto příkazu Spustit `docker images` zobrazíte seznam imagí, které jsou nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="090d9-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="090d9-172">Všimněte si, že dvě bitové kopie sdílet stejný **ID bitové kopie** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090d9-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="090d9-173">Hodnota je mezi obě bitové kopie, protože jediný příkaz v *soubor Dockerfile* byla na základní novou imagí v existující imagi.</span><span class="sxs-lookup"><span data-stu-id="090d9-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="090d9-174">Přidejme dva příkazy, které *soubor Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="090d9-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="090d9-175">Každý příkaz vytvoří novou image vrstvu s poslední příkaz představující obrázek **myimage** úložiště bude odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="090d9-175">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="090d9-176">`COPY` Příkaz sděluje kopírování zadané složky na vašem počítači do složky v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="090d9-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="090d9-177">V tomto příkladu **publikovat** složky je zkopírován do složky s názvem **aplikace** v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-177">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="090d9-178">Další příkaz `ENTRYPOINT`, říká Dockeru konfigurace kontejner pro spuštění jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="090d9-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="090d9-179">Při spuštění kontejneru, `ENTRYPOINT` příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="090d9-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="090d9-180">Až příkaz skončí, automaticky zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="090d9-181">Z terminálu spusťte `docker build -t myimage -f Dockerfile .` a po dokončení příkazu, který, spusťte `docker images`.</span><span class="sxs-lookup"><span data-stu-id="090d9-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

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

<span data-ttu-id="090d9-182">Každý příkaz v *soubor Dockerfile* vygenerované vrstvy a vytvoření **ID bitové kopie**.</span><span class="sxs-lookup"><span data-stu-id="090d9-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="090d9-183">Finální **ID bitové kopie** (bude jiné) je **ddcc6646461b** a dále vytvoříte na základě této image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="090d9-184">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="090d9-184">Create a container</span></span>

<span data-ttu-id="090d9-185">Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="090d9-186">Kontejner můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="090d9-186">You can create a container in two ways.</span></span> <span data-ttu-id="090d9-187">Nejprve vytvořte nový kontejner, který je zastavená.</span><span class="sxs-lookup"><span data-stu-id="090d9-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="090d9-188">`docker create` Příkaz výše vytvoří kontejner na základě **myimage** bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="090d9-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="090d9-189">Výstup tohoto příkazu se dozvíte **ID KONTEJNERU** (bude jiné) vytvořený kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="090d9-190">Pokud chcete zobrazit seznam *všechny* kontejnery, použít `docker ps -a` příkaz:</span><span class="sxs-lookup"><span data-stu-id="090d9-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="090d9-191">Správa kontejneru</span><span class="sxs-lookup"><span data-stu-id="090d9-191">Manage the container</span></span>

<span data-ttu-id="090d9-192">Každý kontejner je přiřazený náhodný název, který vám pomůže odkazovat na instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="090d9-193">Například kontejner, který byl automaticky vytvořen zvolili název **boring_matsumoto** (bude jiný) a tento název je možné spustit kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-193">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="090d9-194">Přepsat automatické název s konkrétní skupinu pomocí `docker create --name` parametru.</span><span class="sxs-lookup"><span data-stu-id="090d9-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="090d9-195">V následujícím příkladu `docker start` příkazu spusťte kontejner a pak používá `docker ps` příkazu můžete zobrazit pouze kontejnery, na kterých běží:</span><span class="sxs-lookup"><span data-stu-id="090d9-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="090d9-196">Podobně platí `docker stop` příkaz zastaví kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="090d9-197">V následujícím příkladu `docker stop` příkaz k zastavení kontejner a pak používá `docker ps` příkazu můžete zobrazit, zda jsou spuštěny žádné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="090d9-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="090d9-198">Připojte se ke kontejneru</span><span class="sxs-lookup"><span data-stu-id="090d9-198">Connect to a container</span></span>

<span data-ttu-id="090d9-199">Po spuštění kontejneru můžete připojit k němu chcete zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="090d9-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="090d9-200">Použití `docker start` a `docker attach` příkazů spusťte kontejner a náhled výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="090d9-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="090d9-201">V tomto příkladu <kbd>CTRL + C</kbd> příkaz slouží k oddělení spuštěný kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-201">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="090d9-202">Ve skutečnosti to může ukončit proces v kontejneru se kontejner zastaví.</span><span class="sxs-lookup"><span data-stu-id="090d9-202">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="090d9-203">`--sig-proxy=false` Parametr zajišťuje, že <kbd>CTRL + C</kbd> nezpůsobí ukončení procesu v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="090d9-204">Chcete-li ověřit, že je stále spuštěna a počítání znovu připojte po odpojení z kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="090d9-205">Odstranit kontejner</span><span class="sxs-lookup"><span data-stu-id="090d9-205">Delete a container</span></span>

<span data-ttu-id="090d9-206">Pro účely tohoto článku už nechcete, jenom předsazení kolem nicneděláním kontejnery.</span><span class="sxs-lookup"><span data-stu-id="090d9-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="090d9-207">Odstraňte kontejner, který jste předtím vytvořili.</span><span class="sxs-lookup"><span data-stu-id="090d9-207">Delete the container you previously created.</span></span> <span data-ttu-id="090d9-208">Pokud je kontejner spuštěný, zastavte ho.</span><span class="sxs-lookup"><span data-stu-id="090d9-208">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="090d9-209">Následující příklad vypíše všechny kontejnery.</span><span class="sxs-lookup"><span data-stu-id="090d9-209">The following example lists all containers.</span></span> <span data-ttu-id="090d9-210">Poté použije `docker rm` příkaz odstranit kontejner a poté ověří podruhé pro všechny spuštěné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="090d9-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="090d9-211">Najednou</span><span class="sxs-lookup"><span data-stu-id="090d9-211">Single run</span></span>

<span data-ttu-id="090d9-212">Docker nabízí `docker run` příkaz pro vytvoření a spuštění kontejneru jako jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="090d9-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="090d9-213">Tento příkaz se eliminuje potřeba spustit `docker create` a potom `docker start`.</span><span class="sxs-lookup"><span data-stu-id="090d9-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="090d9-214">Můžete také nastavit tento příkaz automaticky odstranit kontejner, když se kontejner zastaví.</span><span class="sxs-lookup"><span data-stu-id="090d9-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="090d9-215">Například použít `docker run -it --rm` provést dva kroky, nejprve aktuální terminálu automaticky použít pro připojení ke kontejneru a pak ji odebrat po dokončení kontejneru:</span><span class="sxs-lookup"><span data-stu-id="090d9-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="090d9-216">S `docker run -it`, <kbd>CTRL + C</kbd> příkaz zastaví proces, který je spuštěn v kontejneru, což zase zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="090d9-217">Vzhledem k tomu, `--rm` nebyl zadán parametr, kontejneru se automaticky odstraní, když se zastaví proces.</span><span class="sxs-lookup"><span data-stu-id="090d9-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="090d9-218">Ověřte, že neexistuje:</span><span class="sxs-lookup"><span data-stu-id="090d9-218">Verify that it does not exist:</span></span>

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="090d9-219">Změnit vstupní bod</span><span class="sxs-lookup"><span data-stu-id="090d9-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="090d9-220">`docker run` Příkaz také umožňuje upravovat `ENTRYPOINT` příkaz *soubor Dockerfile* a spusťte něco jiného, ale pouze pro tento kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="090d9-221">Například použijte následující příkaz pro spuštění `bash` nebo `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="090d9-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="090d9-222">Podle potřeby upravte příkaz.</span><span class="sxs-lookup"><span data-stu-id="090d9-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="090d9-223">Windows</span><span class="sxs-lookup"><span data-stu-id="090d9-223">Windows</span></span>
<span data-ttu-id="090d9-224">V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="090d9-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="090d9-225"><kbd>CTRL + C</kbd> stisknutí ukončit proces a zastavení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-225"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="090d9-226">Linux</span><span class="sxs-lookup"><span data-stu-id="090d9-226">Linux</span></span>

<span data-ttu-id="090d9-227">V tomto příkladu `ENTRYPOINT` se změní na `bash`.</span><span class="sxs-lookup"><span data-stu-id="090d9-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="090d9-228">`quit` Po spuštění příkazu, který ukončí proces a zastavit kontejner.</span><span class="sxs-lookup"><span data-stu-id="090d9-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="090d9-229">Základní příkazy</span><span class="sxs-lookup"><span data-stu-id="090d9-229">Essential commands</span></span>

<span data-ttu-id="090d9-230">Docker má mnoho různých příkazů, které se týkají, co byste chtěli provést v kontejneru a obrázky.</span><span class="sxs-lookup"><span data-stu-id="090d9-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="090d9-231">Tyto příkazy Dockeru jsou nezbytné ke správě kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="090d9-231">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="090d9-232">sestavení dockeru</span><span class="sxs-lookup"><span data-stu-id="090d9-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="090d9-233">docker, spusťte</span><span class="sxs-lookup"><span data-stu-id="090d9-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="090d9-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="090d9-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="090d9-235">docker stop</span><span class="sxs-lookup"><span data-stu-id="090d9-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="090d9-236">docker rm</span><span class="sxs-lookup"><span data-stu-id="090d9-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="090d9-237">rmi dockeru</span><span class="sxs-lookup"><span data-stu-id="090d9-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="090d9-238">image dockeru</span><span class="sxs-lookup"><span data-stu-id="090d9-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="090d9-239">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="090d9-239">Clean up resources</span></span>

<span data-ttu-id="090d9-240">Během tohoto kurzu jste vytvořili kontejnery a obrázky.</span><span class="sxs-lookup"><span data-stu-id="090d9-240">During this tutorial you created containers and images.</span></span> <span data-ttu-id="090d9-241">Pokud chcete, odstraňte tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="090d9-241">If you want, delete these resources.</span></span> <span data-ttu-id="090d9-242">Pomocí následujících příkazů</span><span class="sxs-lookup"><span data-stu-id="090d9-242">Use the following commands to</span></span>

01. <span data-ttu-id="090d9-243">Vypsat všechny kontejnery</span><span class="sxs-lookup"><span data-stu-id="090d9-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="090d9-244">Zastavte kontejnerů, které jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="090d9-244">Stop containers that are running.</span></span> <span data-ttu-id="090d9-245">`CONTAINER_NAME` Představuje název automaticky přiřazují do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="090d9-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="090d9-246">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="090d9-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="090d9-247">V dalším kroku odstraňte všechny Image, které už nechcete na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="090d9-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="090d9-248">Odstranit image vytvořené vaší *soubor Dockerfile* a potom odstranit image .NET Core *soubor Dockerfile* byl založen na.</span><span class="sxs-lookup"><span data-stu-id="090d9-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="090d9-249">Můžete použít **ID bitové kopie** nebo **úložiště: značka** řetězec ve formátu.</span><span class="sxs-lookup"><span data-stu-id="090d9-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="090d9-250">Použití `docker images` příkazu zobrazte seznam imagí, které jsou nainstalované.</span><span class="sxs-lookup"><span data-stu-id="090d9-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="090d9-251">Soubory bitových kopií může být velký.</span><span class="sxs-lookup"><span data-stu-id="090d9-251">Image files can be large.</span></span> <span data-ttu-id="090d9-252">Obvykle by odeberte dočasné kontejnery, které jste vytvořili při testování a vývoj vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="090d9-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="090d9-253">Obvykle byste mít základní Image s modulem runtime nainstalovat, pokud máte v úmyslu na vytváření další Image podle tohoto modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="090d9-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="090d9-254">Další postup</span><span class="sxs-lookup"><span data-stu-id="090d9-254">Next steps</span></span>

* [<span data-ttu-id="090d9-255">Projděte si kurz ASP.NET Core Mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="090d9-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="090d9-256">Projděte si služby Azure, které podporují kontejnery.</span><span class="sxs-lookup"><span data-stu-id="090d9-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* [<span data-ttu-id="090d9-257">Přečtěte si informace o příkazů souboru Docker.</span><span class="sxs-lookup"><span data-stu-id="090d9-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
* [<span data-ttu-id="090d9-258">Prozkoumejte nástroje kontejneru sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="090d9-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
