---
title: Kontejnerizace aplikace s využitím kurzu Docker
description: V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200025"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="faec7-103">Kurz: kontejnerizace aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="faec7-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="faec7-104">V tomto kurzu se naučíte, jak kontejnerizace aplikaci .NET Core pomocí Docker.</span><span class="sxs-lookup"><span data-stu-id="faec7-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="faec7-105">Kontejnery mají mnoho funkcí a výhod, jako je například neproměnlivá infrastruktura, poskytuje přenosnou architekturu a povoluje škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="faec7-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="faec7-106">Image se dá použít k vytvoření kontejnerů pro místní vývojové prostředí, privátní cloud nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="faec7-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="faec7-107">V tomto kurzu jste:</span><span class="sxs-lookup"><span data-stu-id="faec7-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="faec7-108">Vytvoření a publikování jednoduché aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="faec7-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="faec7-109">Vytvoření a konfigurace souboru Dockerfile pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="faec7-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="faec7-110">Sestavení image Dockeru</span><span class="sxs-lookup"><span data-stu-id="faec7-110">Build a Docker image</span></span>
> - <span data-ttu-id="faec7-111">Vytvoření a spuštění kontejneru Docker</span><span class="sxs-lookup"><span data-stu-id="faec7-111">Create and run a Docker container</span></span>

<span data-ttu-id="faec7-112">Porozumíte sestavení kontejneru Docker a nasazování úloh pro aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="faec7-113">*Platforma Docker* používá *modul Docker* k rychlému sestavování a zabalení aplikací jako *imagí Docker*.</span><span class="sxs-lookup"><span data-stu-id="faec7-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="faec7-114">Tyto image jsou napsané ve formátu *souboru Dockerfile* , aby je bylo možné nasadit a spustit v vrstveném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="faec7-115">Tento kurz **není** pro aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="faec7-116">Pokud používáte ASP.NET Core, přečtěte si kurz týkající se [kontejnerizace ASP.NET Core aplikace](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="faec7-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="faec7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="faec7-117">Prerequisites</span></span>

<span data-ttu-id="faec7-118">Nainstalujte následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="faec7-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="faec7-119">[Sada .NET Core 3,1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="faec7-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="faec7-120">Pokud máte nainstalované rozhraní .NET Core, pomocí `dotnet --info` příkazu určete, kterou sadu SDK používáte.</span><span class="sxs-lookup"><span data-stu-id="faec7-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="faec7-121">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="faec7-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="faec7-122">Dočasná pracovní složka pro *souboru Dockerfile* a ukázkovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="faec7-123">V tomto kurzu použijete jako pracovní složku název *Docker – Work* .</span><span class="sxs-lookup"><span data-stu-id="faec7-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="faec7-124">Vytvoření aplikace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="faec7-124">Create .NET Core app</span></span>

<span data-ttu-id="faec7-125">Potřebujete aplikaci .NET Core, kterou bude kontejner Docker spustit.</span><span class="sxs-lookup"><span data-stu-id="faec7-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="faec7-126">Otevřete terminál, vytvořte pracovní složku, pokud jste to ještě neudělali, a zadejte ji.</span><span class="sxs-lookup"><span data-stu-id="faec7-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="faec7-127">V pracovní složce spusťte následující příkaz, který vytvoří nový projekt v podadresáři s názvem *App*:</span><span class="sxs-lookup"><span data-stu-id="faec7-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="faec7-128">Váš strom složek bude vypadat následovně:</span><span class="sxs-lookup"><span data-stu-id="faec7-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="faec7-129">`dotnet new` Příkaz vytvoří novou složku s názvem *App* a vygeneruje konzolovou aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="faec7-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="faec7-130">Změňte adresáře a přejděte do složky *aplikace* z relace terminálu.</span><span class="sxs-lookup"><span data-stu-id="faec7-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="faec7-131">Aplikaci spustíte `dotnet run` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="faec7-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="faec7-132">Aplikace se spustí a vytiskne `Hello World!` se pod příkazem:</span><span class="sxs-lookup"><span data-stu-id="faec7-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="faec7-133">Výchozí šablona vytvoří aplikaci, která se tiskne do terminálu a následně se okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="faec7-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="faec7-134">V tomto kurzu použijete aplikaci, která bude mít neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="faec7-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="faec7-135">V textovém editoru otevřete soubor *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="faec7-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="faec7-136">Pokud používáte Visual Studio Code, v předchozí relaci terminálu zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="faec7-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```
> code .
> ```
>
> <span data-ttu-id="faec7-137">Tím se otevře složka *aplikace* , která obsahuje projekt v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="faec7-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="faec7-138">*Program.cs* by měl vypadat jako následující kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="faec7-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
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

<span data-ttu-id="faec7-139">Nahraďte soubor následujícím kódem, který počítá čísla každou sekundu:</span><span class="sxs-lookup"><span data-stu-id="faec7-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="faec7-140">Uložte soubor a otestujte program znovu pomocí `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="faec7-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="faec7-141">Mějte na paměti, že tato aplikace bude běžet po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="faec7-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="faec7-142">K zastavení použijte příkaz zrušit <kbd>CTRL + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="faec7-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="faec7-143">Následuje příklad výstupu:</span><span class="sxs-lookup"><span data-stu-id="faec7-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="faec7-144">Pokud předáte číslo do příkazového řádku do aplikace, bude se počítat jenom s touto velikostí a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="faec7-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="faec7-145">Zkuste to s `dotnet run -- 5` počtem až pěti.</span><span class="sxs-lookup"><span data-stu-id="faec7-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faec7-146">Jakékoli parametry po `--` nejsou předány do `dotnet run` příkazu a místo toho jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="faec7-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="faec7-147">Publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="faec7-147">Publish .NET Core app</span></span>

<span data-ttu-id="faec7-148">Před přidáním aplikace .NET Core do image Docker je třeba nejdřív publikovat.</span><span class="sxs-lookup"><span data-stu-id="faec7-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="faec7-149">Nejlepší je nechat kontejner spustit publikovanou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="faec7-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="faec7-150">Pokud chcete aplikaci publikovat, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="faec7-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="faec7-151">Tento příkaz zkompiluje vaši aplikaci do složky pro *publikování* .</span><span class="sxs-lookup"><span data-stu-id="faec7-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="faec7-152">Cesta ke složce pro *publikování* z pracovní složky by měla být`.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="faec7-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="faec7-153">Windows</span><span class="sxs-lookup"><span data-stu-id="faec7-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="faec7-154">Ve složce *aplikace* Získejte výpis adresáře složky pro publikování, abyste ověřili, že byl vytvořen soubor *Netcore. Docker. dll* .</span><span class="sxs-lookup"><span data-stu-id="faec7-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="faec7-155">Linux</span><span class="sxs-lookup"><span data-stu-id="faec7-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="faec7-156">Pomocí `ls` příkazu Získejte výpis adresáře a ověřte, zda byl vytvořen soubor *Netcore. Docker. dll* .</span><span class="sxs-lookup"><span data-stu-id="faec7-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="faec7-157">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="faec7-157">Create the Dockerfile</span></span>

<span data-ttu-id="faec7-158">Soubor *souboru Dockerfile* používá `docker build` příkaz k vytvoření image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="faec7-159">Tento soubor je textový soubor s názvem *souboru Dockerfile* , který nemá příponu.</span><span class="sxs-lookup"><span data-stu-id="faec7-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="faec7-160">Vytvořte soubor s názvem *souboru Dockerfile* v adresáři obsahujícím *. csproj* a otevřete ho v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="faec7-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="faec7-161">Tento kurz použije bitovou kopii ASP.NET Core Runtime (která obsahuje bitovou kopii .NET Core Runtime) a odpovídá konzolové aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="faec7-162">Bitová kopie ASP.NET Core Runtime se tady používá záměrně, i když `mcr.microsoft.com/dotnet/core/runtime:3.1` se image mohla použít.</span><span class="sxs-lookup"><span data-stu-id="faec7-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/core/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="faec7-163">`FROM` Klíčové slovo vyžaduje plně kvalifikovaný název Image kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="faec7-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="faec7-164">Microsoft Container Registry (MCR, mcr.microsoft.com) je syndikátní služby Docker Hub, která hostuje veřejně přístupné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="faec7-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="faec7-165">`dotnet/core` Segment je úložiště kontejneru, kde jako `aspnet` segment je název Image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="faec7-166">Obrázek je označený jako `3.1`, který se používá pro správu verzí.</span><span class="sxs-lookup"><span data-stu-id="faec7-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="faec7-167">Proto `mcr.microsoft.com/dotnet/core/aspnet:3.1` je modul runtime .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="faec7-167">Thus, `mcr.microsoft.com/dotnet/core/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="faec7-168">Ujistěte se, že si vyžádáte verzi modulu runtime, která odpovídá modulu runtime, který cílí na vaši sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="faec7-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="faec7-169">Například aplikace vytvořená v předchozím oddílu používala sadu .NET Core 3,1 SDK a základní image, na kterou odkazuje *souboru Dockerfile* , jsou označené **3,1**.</span><span class="sxs-lookup"><span data-stu-id="faec7-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="faec7-170">Uložte soubor *souboru Dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="faec7-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="faec7-171">Adresářová struktura pracovní složky by měla vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="faec7-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="faec7-172">Některé soubory hlubší úrovně a složky byly vynechány, aby bylo možné ušetřit místo v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="faec7-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="faec7-173">Z terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="faec7-173">From your terminal, run the following command:</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="faec7-174">Docker zpracuje každý řádek v *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="faec7-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="faec7-175">`.` V `docker build` příkazu dá Docker pokyn k použití aktuální složky k vyhledání *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="faec7-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="faec7-176">Tento příkaz sestaví image a vytvoří místní úložiště s názvem **Counter-image** , která odkazuje na tuto image.</span><span class="sxs-lookup"><span data-stu-id="faec7-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="faec7-177">Po dokončení tohoto příkazu spusťte `docker images` příkaz a zobrazí se seznam nainstalovaných imagí:</span><span class="sxs-lookup"><span data-stu-id="faec7-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="faec7-178">Všimněte si, že tyto dva obrázky sdílejí stejnou hodnotu **ID obrázku** .</span><span class="sxs-lookup"><span data-stu-id="faec7-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="faec7-179">Tato hodnota je stejná mezi oběma obrazci, protože jediný příkaz v *souboru Dockerfile* byl založen na novém obrázku na stávající imagi.</span><span class="sxs-lookup"><span data-stu-id="faec7-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="faec7-180">Pojďme do *souboru Dockerfile*přidat tři příkazy.</span><span class="sxs-lookup"><span data-stu-id="faec7-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="faec7-181">Každý příkaz vytvoří novou vrstvu obrázku s posledním příkazem, který představuje vstupní body úložiště **počítadla a obrázku** .</span><span class="sxs-lookup"><span data-stu-id="faec7-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="faec7-182">`COPY` Příkaz vyzve Docker ke zkopírování zadané složky ve vašem počítači do složky v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="faec7-183">V tomto příkladu je složka pro *publikování* zkopírována do složky s názvem *App* v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="faec7-184">`WORKDIR` Příkaz změní **aktuální adresář** uvnitř kontejneru do *aplikace*.</span><span class="sxs-lookup"><span data-stu-id="faec7-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="faec7-185">Následující příkaz `ENTRYPOINT`instruuje Docker ke konfiguraci kontejneru tak, aby běžel jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="faec7-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="faec7-186">Po spuštění kontejneru se `ENTRYPOINT` příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="faec7-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="faec7-187">Po ukončení tohoto příkazu se kontejner automaticky zastaví.</span><span class="sxs-lookup"><span data-stu-id="faec7-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="faec7-188">V terminálu spusťte `docker build -t counter-image -f Dockerfile .` příkaz a po jeho dokončení spusťte `docker images`příkaz.</span><span class="sxs-lookup"><span data-stu-id="faec7-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="faec7-189">Každý příkaz v *souboru Dockerfile* vygeneroval vrstvu a vytvořila **ID obrázku**.</span><span class="sxs-lookup"><span data-stu-id="faec7-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="faec7-190">Konečné **ID image** (bude se lišit) bude **cd11c3df9b19** a dál vytvoříte kontejner na základě tohoto obrázku.</span><span class="sxs-lookup"><span data-stu-id="faec7-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="faec7-191">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="faec7-191">Create a container</span></span>

<span data-ttu-id="faec7-192">Teď, když máte image, která obsahuje vaši aplikaci, můžete vytvořit kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="faec7-193">Kontejner můžete vytvořit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="faec7-193">You can create a container in two ways.</span></span> <span data-ttu-id="faec7-194">Nejdřív vytvořte nový kontejner, který se zastaví.</span><span class="sxs-lookup"><span data-stu-id="faec7-194">First, create a new container that is stopped.</span></span>

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="faec7-195">Výše `docker create` uvedený příkaz vytvoří kontejner založený na obrázku **čítače-obrázek** .</span><span class="sxs-lookup"><span data-stu-id="faec7-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="faec7-196">Výstup tohoto příkazu ukazuje **ID kontejneru** (bude se lišit) vytvořeného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="faec7-197">Chcete-li zobrazit seznam *všech* kontejnerů, použijte `docker ps -a` příkaz:</span><span class="sxs-lookup"><span data-stu-id="faec7-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="faec7-198">Správa kontejneru</span><span class="sxs-lookup"><span data-stu-id="faec7-198">Manage the container</span></span>

<span data-ttu-id="faec7-199">Kontejner byl vytvořen s konkrétním názvem `core-counter`, tento název se používá ke správě kontejneru.</span><span class="sxs-lookup"><span data-stu-id="faec7-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="faec7-200">Následující příklad používá `docker start` příkaz ke spuštění kontejneru a poté používá `docker ps` příkaz k zobrazení pouze kontejnerů, které jsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="faec7-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="faec7-201">Podobně `docker stop` příkaz zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="faec7-202">Následující příklad používá `docker stop` příkaz k zastavení kontejneru a poté používá `docker ps` příkaz k zobrazení, že žádné kontejnery nejsou spuštěny:</span><span class="sxs-lookup"><span data-stu-id="faec7-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="faec7-203">Připojit ke kontejneru</span><span class="sxs-lookup"><span data-stu-id="faec7-203">Connect to a container</span></span>

<span data-ttu-id="faec7-204">Po spuštění kontejneru se k němu můžete připojit a zobrazit výstup.</span><span class="sxs-lookup"><span data-stu-id="faec7-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="faec7-205">Použijte příkazy `docker start` a `docker attach` ke spuštění kontejneru a k prohlížení výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="faec7-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="faec7-206">V tomto příkladu se k odpojení od běžícího kontejneru používá <kbd>Klávesová zkratka CTRL + C</kbd> .</span><span class="sxs-lookup"><span data-stu-id="faec7-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="faec7-207">Tato klávesová zkratka ukončí proces v kontejneru, pokud není uvedeno jinak, což by zastavilo kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="faec7-208">`--sig-proxy=false` Parametr zajistí, že <kbd>CTRL + C</kbd> nebude proces v kontejneru zastavit.</span><span class="sxs-lookup"><span data-stu-id="faec7-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="faec7-209">Po odpojení od kontejneru znovu připojte, abyste ověřili, že pořád běží a počítá se.</span><span class="sxs-lookup"><span data-stu-id="faec7-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="faec7-210">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="faec7-210">Delete a container</span></span>

<span data-ttu-id="faec7-211">Pro účely tohoto článku nechcete, aby kontejnery právě neprováděly žádné akce.</span><span class="sxs-lookup"><span data-stu-id="faec7-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="faec7-212">Odstraňte kontejner, který jste dříve vytvořili.</span><span class="sxs-lookup"><span data-stu-id="faec7-212">Delete the container you previously created.</span></span> <span data-ttu-id="faec7-213">Pokud je kontejner spuštěný, zastavte ho.</span><span class="sxs-lookup"><span data-stu-id="faec7-213">If the container is running, stop it.</span></span>

```Docker
docker stop core-counter
```

<span data-ttu-id="faec7-214">Následující příklad zobrazí seznam všech kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="faec7-214">The following example lists all containers.</span></span> <span data-ttu-id="faec7-215">Pak pomocí příkazu tento `docker rm` kontejner odstraní a pak u všech spuštěných kontejnerů zkontroluje druhou dobu.</span><span class="sxs-lookup"><span data-stu-id="faec7-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="faec7-216">Jeden běh</span><span class="sxs-lookup"><span data-stu-id="faec7-216">Single run</span></span>

<span data-ttu-id="faec7-217">Docker poskytuje `docker run` příkaz pro vytvoření a spuštění kontejneru jako jediného příkazu.</span><span class="sxs-lookup"><span data-stu-id="faec7-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="faec7-218">Tento příkaz eliminuje nutnost spuštění `docker create` a pak. `docker start`</span><span class="sxs-lookup"><span data-stu-id="faec7-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="faec7-219">Tento příkaz lze také nastavit tak, aby při zastavení kontejneru automaticky odstranil kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="faec7-220">Například použijte `docker run -it --rm` k provedení dvou věcí, nejdřív, automatické použití aktuálního terminálu k připojení ke kontejneru a po dokončení kontejneru ho odeberte:</span><span class="sxs-lookup"><span data-stu-id="faec7-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="faec7-221">Kontejner také předává parametry do provádění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="faec7-222">K tomu, aby aplikace .NET Core mohla počítat jenom 3 průchody 3.</span><span class="sxs-lookup"><span data-stu-id="faec7-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="faec7-223">V `docker run -it`systému, příkaz <kbd>CTRL + C</kbd> zastaví proces, který je spuštěn v kontejneru, který zase zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="faec7-224">Vzhledem k `--rm` tomu, že byl zadán parametr, kontejner je automaticky odstraněn při zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="faec7-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="faec7-225">Ověřte, že neexistuje:</span><span class="sxs-lookup"><span data-stu-id="faec7-225">Verify that it doesn't exist:</span></span>

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="faec7-226">Změnit vstupní bod</span><span class="sxs-lookup"><span data-stu-id="faec7-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="faec7-227">`docker run` Příkaz také umožňuje upravit `ENTRYPOINT` příkaz z *souboru Dockerfile* a spustit něco jiného, ale pouze pro tento kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="faec7-228">Například použijte následující příkaz ke spuštění `bash` nebo. `cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="faec7-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="faec7-229">V případě potřeby upravte příkaz.</span><span class="sxs-lookup"><span data-stu-id="faec7-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="faec7-230">Windows</span><span class="sxs-lookup"><span data-stu-id="faec7-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="faec7-231">V tomto příkladu `ENTRYPOINT` se změní na `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="faec7-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="faec7-232">Stisknutím <kbd>kombinace kláves CTRL + C</kbd> ukončíte proces a zastavíte kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

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

#### <a name="linux"></a>[<span data-ttu-id="faec7-233">Linux</span><span class="sxs-lookup"><span data-stu-id="faec7-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="faec7-234">V tomto příkladu `ENTRYPOINT` se změní na `bash`.</span><span class="sxs-lookup"><span data-stu-id="faec7-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="faec7-235">`exit` Příkaz se spustí, který ukončí proces a zastaví kontejner.</span><span class="sxs-lookup"><span data-stu-id="faec7-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="faec7-236">Důležité příkazy</span><span class="sxs-lookup"><span data-stu-id="faec7-236">Essential commands</span></span>

<span data-ttu-id="faec7-237">Docker má mnoho různých příkazů, které umožňují vytvářet, spravovat a pracovat s kontejnery a obrázky.</span><span class="sxs-lookup"><span data-stu-id="faec7-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="faec7-238">Tyto příkazy Docker jsou zásadní pro správu vašich kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="faec7-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="faec7-239">docker build</span><span class="sxs-lookup"><span data-stu-id="faec7-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="faec7-240">spuštění Docker</span><span class="sxs-lookup"><span data-stu-id="faec7-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="faec7-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="faec7-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="faec7-242">zastavení Docker</span><span class="sxs-lookup"><span data-stu-id="faec7-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="faec7-243">Docker RM</span><span class="sxs-lookup"><span data-stu-id="faec7-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="faec7-244">Docker RMI</span><span class="sxs-lookup"><span data-stu-id="faec7-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="faec7-245">Obrázek Docker</span><span class="sxs-lookup"><span data-stu-id="faec7-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="faec7-246">Vyčištění prostředků</span><span class="sxs-lookup"><span data-stu-id="faec7-246">Clean up resources</span></span>

<span data-ttu-id="faec7-247">Během tohoto kurzu jste vytvořili kontejnery a image.</span><span class="sxs-lookup"><span data-stu-id="faec7-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="faec7-248">Pokud chcete, tyto prostředky odstraňte.</span><span class="sxs-lookup"><span data-stu-id="faec7-248">If you want, delete these resources.</span></span> <span data-ttu-id="faec7-249">Následující příkazy použijte k</span><span class="sxs-lookup"><span data-stu-id="faec7-249">Use the following commands to</span></span>

01. <span data-ttu-id="faec7-250">Vypsat všechny kontejnery</span><span class="sxs-lookup"><span data-stu-id="faec7-250">List all containers</span></span>

    ```Docker
    docker ps -a
    ```

02. <span data-ttu-id="faec7-251">Zastavte kontejnery, které jsou spuštěné podle jejich názvu.</span><span class="sxs-lookup"><span data-stu-id="faec7-251">Stop containers that are running by their name.</span></span>

    ```Docker
    docker stop counter-image
    ```

03. <span data-ttu-id="faec7-252">Odstranění kontejneru</span><span class="sxs-lookup"><span data-stu-id="faec7-252">Delete the container</span></span>

    ```Docker
    docker rm counter-image
    ```

<span data-ttu-id="faec7-253">Pak na počítači odstraňte všechny image, které už nechcete.</span><span class="sxs-lookup"><span data-stu-id="faec7-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="faec7-254">Odstraňte image vytvořenou *souboru Dockerfile* a pak odstraňte image .NET Core, na které byl *souboru Dockerfile* založen.</span><span class="sxs-lookup"><span data-stu-id="faec7-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="faec7-255">Můžete použít **ID obrázku** nebo **úložiště:** řetězec ve formátu značek.</span><span class="sxs-lookup"><span data-stu-id="faec7-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="faec7-256">Pomocí `docker images` příkazu zobrazte seznam nainstalovaných imagí.</span><span class="sxs-lookup"><span data-stu-id="faec7-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="faec7-257">Soubory obrázků můžou být velké.</span><span class="sxs-lookup"><span data-stu-id="faec7-257">Image files can be large.</span></span> <span data-ttu-id="faec7-258">Obvykle byste odebrali dočasné kontejnery, které jste vytvořili při testování a vývoji vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="faec7-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="faec7-259">Při plánování vytváření dalších imagí na základě tohoto modulu runtime obvykle zachováte základní image s nainstalovaným modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="faec7-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="faec7-260">Další kroky</span><span class="sxs-lookup"><span data-stu-id="faec7-260">Next steps</span></span>

- [<span data-ttu-id="faec7-261">Naučte se, jak kontejnerizace aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="faec7-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="faec7-262">Vyzkoušejte si kurz ASP.NET Core mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="faec7-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="faec7-263">Projděte si služby Azure, které podporují kontejnery.</span><span class="sxs-lookup"><span data-stu-id="faec7-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="faec7-264">Přečtěte si o příkazech souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="faec7-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="faec7-265">Prozkoumejte nástroje kontejnerů pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="faec7-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
