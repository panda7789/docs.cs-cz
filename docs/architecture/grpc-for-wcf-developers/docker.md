---
title: Docker – gRPC pro vývojáře WCF
description: Vytváření imagí Docker pro aplikace ASP.NET Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: d23dc46526183b459c36f11bae4def8b1c9b9410
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711304"
---
# <a name="create-docker-images"></a><span data-ttu-id="557cb-103">Vytváření imagí Docker</span><span class="sxs-lookup"><span data-stu-id="557cb-103">Create Docker images</span></span>

<span data-ttu-id="557cb-104">Tato část se zabývá vytvářením imagí Docker pro aplikace ASP.NET Core gRPC, které jsou připravené ke spuštění v Docker, Kubernetes nebo v jiných kontejnerových prostředích.</span><span class="sxs-lookup"><span data-stu-id="557cb-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="557cb-105">Použitá ukázková aplikace s ASP.NET Core webovou aplikací MVC a službou gRPC je k dispozici v úložišti [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="557cb-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="557cb-106">Základní image Microsoft pro aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="557cb-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="557cb-107">Microsoft poskytuje řadu základních imagí pro sestavování a spouštění aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="557cb-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="557cb-108">Pokud chcete vytvořit image ASP.NET Core 3,0, použijete dvě základní Image:</span><span class="sxs-lookup"><span data-stu-id="557cb-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span> 

- <span data-ttu-id="557cb-109">Image sady SDK pro sestavování a publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="557cb-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="557cb-110">Bitová kopie modulu runtime pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="557cb-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="557cb-111">Obrázek</span><span class="sxs-lookup"><span data-stu-id="557cb-111">Image</span></span> | <span data-ttu-id="557cb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="557cb-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="557cb-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="557cb-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="557cb-114">Pro sestavování aplikací pomocí `docker build`.</span><span class="sxs-lookup"><span data-stu-id="557cb-114">For building applications with `docker build`.</span></span> <span data-ttu-id="557cb-115">Nedá se použít v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="557cb-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="557cb-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="557cb-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="557cb-117">Obsahuje závislosti modulu runtime a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="557cb-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="557cb-118">Pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="557cb-118">For production.</span></span> |

<span data-ttu-id="557cb-119">Pro každý obrázek jsou k dispozici čtyři varianty založené na různých distribucích systému Linux, které jsou odlišeny pomocí značek.</span><span class="sxs-lookup"><span data-stu-id="557cb-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="557cb-120">Značky obrázku</span><span class="sxs-lookup"><span data-stu-id="557cb-120">Image tag(s)</span></span> | <span data-ttu-id="557cb-121">Linux</span><span class="sxs-lookup"><span data-stu-id="557cb-121">Linux</span></span> | <span data-ttu-id="557cb-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="557cb-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="557cb-123">3,0 – Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="557cb-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="557cb-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="557cb-124">Debian 10</span></span> | <span data-ttu-id="557cb-125">Výchozí obrázek, pokud není zadána varianta operačního systému.</span><span class="sxs-lookup"><span data-stu-id="557cb-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="557cb-126">3,0 – Alpine</span><span class="sxs-lookup"><span data-stu-id="557cb-126">3.0-alpine</span></span> | <span data-ttu-id="557cb-127">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="557cb-127">Alpine 3.9</span></span> | <span data-ttu-id="557cb-128">Obrázky Alpine Base jsou mnohem menší než Debian nebo Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="557cb-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="557cb-129">3,0 – disco</span><span class="sxs-lookup"><span data-stu-id="557cb-129">3.0-disco</span></span> | <span data-ttu-id="557cb-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="557cb-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="557cb-131">3,0 – Bionic</span><span class="sxs-lookup"><span data-stu-id="557cb-131">3.0-bionic</span></span> | <span data-ttu-id="557cb-132">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="557cb-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="557cb-133">Základní obrázek Alpine je okolo 100 MB, v porovnání s 200 MB pro Image Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="557cb-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="557cb-134">Některé softwarové balíčky nebo knihovny nemusí být k dispozici ve správě balíčků Alpine.</span><span class="sxs-lookup"><span data-stu-id="557cb-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="557cb-135">Pokud si nejste jistí, která image se má použít, měli byste zvolit výchozí Debian.</span><span class="sxs-lookup"><span data-stu-id="557cb-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="557cb-136">Ujistěte se, že používáte stejnou variantu systému Linux pro sestavení a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="557cb-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="557cb-137">Aplikace sestavené a publikované na jednom variantě nemusí fungovat na jiném.</span><span class="sxs-lookup"><span data-stu-id="557cb-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="557cb-138">Vytvoření image Docker</span><span class="sxs-lookup"><span data-stu-id="557cb-138">Create a Docker image</span></span>

<span data-ttu-id="557cb-139">Image Docker je definovaná pomocí *souboru Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="557cb-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="557cb-140">Jedná se o textový soubor, který obsahuje všechny příkazy potřebné k sestavení aplikace a instalaci všech závislostí, které jsou požadovány pro vytvoření nebo spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="557cb-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="557cb-141">Následující příklad ukazuje nejjednodušší souboru Dockerfile pro aplikaci ASP.NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="557cb-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="557cb-142">Souboru Dockerfile má dvě části: první používá základní image `sdk` k sestavení a publikování aplikace. Druhá vytvoří bitovou kopii modulu runtime ze základu `aspnet`.</span><span class="sxs-lookup"><span data-stu-id="557cb-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="557cb-143">Důvodem je to, že bitová kopie `sdk` o velikosti přibližně 900 MB, v porovnání s přibližně 200 MB pro bitovou kopii za běhu a většinu jejího obsahu nepotřebnou za běhu.</span><span class="sxs-lookup"><span data-stu-id="557cb-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="557cb-144">Kroky sestavení</span><span class="sxs-lookup"><span data-stu-id="557cb-144">The build steps</span></span>

| <span data-ttu-id="557cb-145">Krok</span><span class="sxs-lookup"><span data-stu-id="557cb-145">Step</span></span> | <span data-ttu-id="557cb-146">Popis</span><span class="sxs-lookup"><span data-stu-id="557cb-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="557cb-147">Deklaruje základní obrázek a přiřadí alias `builder`.</span><span class="sxs-lookup"><span data-stu-id="557cb-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="557cb-148">Vytvoří adresář `/src` a nastaví ho jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="557cb-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="557cb-149">Zkopíruje vše pod aktuálním adresářem v hostiteli do aktuálního adresáře v imagi.</span><span class="sxs-lookup"><span data-stu-id="557cb-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="557cb-150">Obnoví všechny externí balíčky (ASP.NET Core 3,0 Framework je předem nainstalovaná s SDK).</span><span class="sxs-lookup"><span data-stu-id="557cb-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="557cb-151">Vytvoří a publikuje sestavení pro vydání.</span><span class="sxs-lookup"><span data-stu-id="557cb-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="557cb-152">Všimněte si, že příznak `--runtime` není povinný.</span><span class="sxs-lookup"><span data-stu-id="557cb-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="557cb-153">Kroky bitové kopie modulu runtime</span><span class="sxs-lookup"><span data-stu-id="557cb-153">The runtime image steps</span></span>

| <span data-ttu-id="557cb-154">Krok</span><span class="sxs-lookup"><span data-stu-id="557cb-154">Step</span></span> | <span data-ttu-id="557cb-155">Popis</span><span class="sxs-lookup"><span data-stu-id="557cb-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="557cb-156">Deklaruje novou základní image.</span><span class="sxs-lookup"><span data-stu-id="557cb-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="557cb-157">Vytvoří adresář `/app` a nastaví ho jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="557cb-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="557cb-158">Zkopíruje publikovanou aplikaci z předchozího obrázku pomocí aliasu `builder` z prvního `FROM` řádku.</span><span class="sxs-lookup"><span data-stu-id="557cb-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="557cb-159">Nastaví příkaz, který se spustí při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="557cb-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="557cb-160">Příkaz `dotnet` v imagi modulu runtime může spouštět pouze soubory DLL.</span><span class="sxs-lookup"><span data-stu-id="557cb-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="557cb-161">HTTPS v Docker</span><span class="sxs-lookup"><span data-stu-id="557cb-161">HTTPS in Docker</span></span>

<span data-ttu-id="557cb-162">Základní image Microsoftu pro Docker nastaví proměnnou prostředí `ASPNETCORE_URLS` na `http://+:80`, což znamená, že Kestrel na tomto portu běží bez protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="557cb-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="557cb-163">Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [samoobslužných aplikacích gRPC](self-hosted.md)), měli byste ho přepsat.</span><span class="sxs-lookup"><span data-stu-id="557cb-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="557cb-164">Nastavte proměnnou prostředí v rámci souboru Dockerfile pro vytvoření bitové kopie modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="557cb-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="557cb-165">Soubor. dockerignore</span><span class="sxs-lookup"><span data-stu-id="557cb-165">The .dockerignore file</span></span>

<span data-ttu-id="557cb-166">Podobně jako `.gitignore` soubory, které vyloučí určité soubory a adresáře ze správy zdrojového kódu, lze `.dockerignore` soubor použít k vyloučení souborů a adresářů, které se zkopírují do bitové kopie během sestavení.</span><span class="sxs-lookup"><span data-stu-id="557cb-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="557cb-167">Tím se nejen ukládá pouze kopírování času, ale může se taky vyhnout nějakým chybám, které vyplývají z toho, že se `obj` adresář z počítače zkopíroval do image.</span><span class="sxs-lookup"><span data-stu-id="557cb-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="557cb-168">Do souboru `.dockerignore` byste měli přidat položky pro `bin` a `obj`.</span><span class="sxs-lookup"><span data-stu-id="557cb-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="557cb-169">Sestavení image</span><span class="sxs-lookup"><span data-stu-id="557cb-169">Build the image</span></span>

<span data-ttu-id="557cb-170">Pro řešení s jednou aplikací, a proto jediným souboru Dockerfile, je nejjednodušší umístit souboru Dockerfile do základního adresáře.</span><span class="sxs-lookup"><span data-stu-id="557cb-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="557cb-171">Jinými slovy, umístěte je do stejného adresáře jako soubor `.sln`.</span><span class="sxs-lookup"><span data-stu-id="557cb-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="557cb-172">V takovém případě pro sestavení image použijte následující příkaz `docker build` z adresáře obsahujícího rozhraní souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="557cb-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="557cb-173">Nematoucí název `--tag` příznakem (který může být zkrácen na `-t`) určuje celý název obrázku, včetně skutečné značky, je-li tento parametr zadán.</span><span class="sxs-lookup"><span data-stu-id="557cb-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="557cb-174">`.` na konci určuje kontext, ve kterém se bude sestavení spouštět; aktuální pracovní adresář pro příkazy `COPY` v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="557cb-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="557cb-175">Pokud máte více aplikací v rámci jednoho řešení, můžete souboru Dockerfile pro každou aplikaci ve vlastní složce vedle souboru `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="557cb-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="557cb-176">Stále byste měli spustit příkaz `docker build` ze základního adresáře, aby bylo zajištěno, že řešení a všechny projekty budou zkopírovány do obrázku.</span><span class="sxs-lookup"><span data-stu-id="557cb-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="557cb-177">Pomocí příznaku `--file` (nebo `-f`) můžete zadat souboru Dockerfile pod aktuálním adresářem.</span><span class="sxs-lookup"><span data-stu-id="557cb-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="557cb-178">Spuštění image v kontejneru na počítači</span><span class="sxs-lookup"><span data-stu-id="557cb-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="557cb-179">Pokud chcete spustit image v místní instanci Docker, použijte příkaz `docker run`.</span><span class="sxs-lookup"><span data-stu-id="557cb-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="557cb-180">Příznak `-ti` připojí váš aktuální terminál k terminálu kontejneru a spustí se v interaktivním režimu.</span><span class="sxs-lookup"><span data-stu-id="557cb-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="557cb-181">`-p 5000:80` zveřejňuje (odkazy) port 80 na kontejneru na port 80 na síťovém rozhraní localhost.</span><span class="sxs-lookup"><span data-stu-id="557cb-181">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="557cb-182">Vložení image do registru</span><span class="sxs-lookup"><span data-stu-id="557cb-182">Push the image to a registry</span></span>

<span data-ttu-id="557cb-183">Až ověříte, že image funguje, nahrajte ji do registru Docker a zpřístupněte ji v dalších systémech.</span><span class="sxs-lookup"><span data-stu-id="557cb-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="557cb-184">Interní sítě budou muset zřídit registr Docker.</span><span class="sxs-lookup"><span data-stu-id="557cb-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="557cb-185">Může to být tak jednoduché jako [image s vlastním `registry`m](https://docs.docker.com/registry/deploying/) , která je k dispozici, a je k dispozici i několik komplexních řešení.</span><span class="sxs-lookup"><span data-stu-id="557cb-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="557cb-186">Pro externí sdílení a cloudové použití jsou k dispozici různé spravované Registry, například [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="557cb-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="557cb-187">Pokud chcete přejít do Docker Hub, nahraďte název bitové kopie vaším uživatelem nebo názvem organizace.</span><span class="sxs-lookup"><span data-stu-id="557cb-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="557cb-188">Pokud chcete přejít do privátního registru, použijte předponu názvu bitové kopie s názvem hostitele registru a názvem organizace.</span><span class="sxs-lookup"><span data-stu-id="557cb-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="557cb-189">Jakmile je bitová kopie v registru, můžete ji nasadit na jednotlivé hostitele Docker nebo na modul pro orchestraci kontejnerů, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="557cb-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="557cb-190">[Předchozí](self-hosted.md)
>[Další](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="557cb-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
