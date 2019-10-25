---
title: Docker – gRPC pro vývojáře WCF
description: Vytváření imagí Docker pro aplikace ASP.NET Core gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cc369da9494ade532187dfc8d19a94a3a037ebab
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846676"
---
# <a name="docker"></a><span data-ttu-id="8efcf-103">Docker</span><span class="sxs-lookup"><span data-stu-id="8efcf-103">Docker</span></span>

<span data-ttu-id="8efcf-104">Tato část se zabývá vytvářením imagí Docker pro aplikace ASP.NET Core gRPC, které jsou připravené ke spuštění v Docker, Kubernetes nebo v jiných kontejnerových prostředích.</span><span class="sxs-lookup"><span data-stu-id="8efcf-104">This section will cover the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="8efcf-105">Použitá ukázková aplikace s ASP.NET Core webovou aplikací MVC a službou gRPC je k dispozici v úložišti [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="8efcf-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="8efcf-106">Základní image Microsoft pro aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8efcf-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="8efcf-107">Microsoft poskytuje řadu základních imagí pro sestavování a spouštění aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8efcf-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="8efcf-108">Chcete-li vytvořit bitovou kopii ASP.NET Core 3,0, jsou použity dvě základní bitové kopie: image sady SDK pro sestavení a publikování aplikace a bitovou kopii modulu runtime pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="8efcf-108">To create an ASP.NET Core 3.0 image, two base images are used: an SDK image to build and publish the application, and a runtime image for deployment.</span></span>

| <span data-ttu-id="8efcf-109">Image</span><span class="sxs-lookup"><span data-stu-id="8efcf-109">Image</span></span> | <span data-ttu-id="8efcf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8efcf-110">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="8efcf-111">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="8efcf-111">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="8efcf-112">Pro sestavování aplikací pomocí `docker build`.</span><span class="sxs-lookup"><span data-stu-id="8efcf-112">For building applications with `docker build`.</span></span> <span data-ttu-id="8efcf-113">Nedá se použít v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8efcf-113">Not to be used in production.</span></span> |
| [<span data-ttu-id="8efcf-114">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="8efcf-114">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="8efcf-115">Obsahuje závislosti modulu runtime a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8efcf-115">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="8efcf-116">Pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="8efcf-116">For production.</span></span> |

<span data-ttu-id="8efcf-117">Pro každý obrázek jsou k dispozici čtyři varianty založené na různých distribucích systému Linux, které jsou odlišeny pomocí značek.</span><span class="sxs-lookup"><span data-stu-id="8efcf-117">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="8efcf-118">Značky obrázku</span><span class="sxs-lookup"><span data-stu-id="8efcf-118">Image tag(s)</span></span> | <span data-ttu-id="8efcf-119">Linux</span><span class="sxs-lookup"><span data-stu-id="8efcf-119">Linux</span></span> | <span data-ttu-id="8efcf-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8efcf-120">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="8efcf-121">3,0 – Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="8efcf-121">3.0-buster, 3.0</span></span> | <span data-ttu-id="8efcf-122">Debian 10</span><span class="sxs-lookup"><span data-stu-id="8efcf-122">Debian 10</span></span> | <span data-ttu-id="8efcf-123">Výchozí obrázek, pokud není zadána varianta operačního systému.</span><span class="sxs-lookup"><span data-stu-id="8efcf-123">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="8efcf-124">3,0 – Alpine</span><span class="sxs-lookup"><span data-stu-id="8efcf-124">3.0-alpine</span></span> | <span data-ttu-id="8efcf-125">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="8efcf-125">Alpine 3.9</span></span> | <span data-ttu-id="8efcf-126">Obrázky Alpine Base jsou mnohem menší než Debian nebo Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8efcf-126">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="8efcf-127">3,0 – disco</span><span class="sxs-lookup"><span data-stu-id="8efcf-127">3.0-disco</span></span> | <span data-ttu-id="8efcf-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="8efcf-128">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="8efcf-129">3,0 – Bionic</span><span class="sxs-lookup"><span data-stu-id="8efcf-129">3.0-bionic</span></span> | <span data-ttu-id="8efcf-130">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="8efcf-130">Ubuntu 18.04</span></span> | |

<span data-ttu-id="8efcf-131">Základní image Alpine je okolo 100 MB, v porovnání s 200 MB pro Image Debian a Ubuntu, ale některé softwarové balíčky nebo knihovny nemusí být k dispozici ve správě balíčků Alpine.</span><span class="sxs-lookup"><span data-stu-id="8efcf-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images, but some software packages or libraries may not be available in Alpine's package management.</span></span> <span data-ttu-id="8efcf-132">Pokud si nejste jistí, která image se má použít, je nejlepší vytvořit výchozí Debian, pokud nemáte přesvědčivou potřebu použít jiný distribuce.</span><span class="sxs-lookup"><span data-stu-id="8efcf-132">If you're not sure which image to use, it's best to stick to the default Debian unless you have a compelling need to use a different distro.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8efcf-133">Ujistěte se, že používáte stejnou variantu systému Linux pro sestavení a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8efcf-133">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="8efcf-134">Aplikace sestavené a publikované na jednom variantě nemusí fungovat na jiném.</span><span class="sxs-lookup"><span data-stu-id="8efcf-134">Applications built and published on one variant may not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="8efcf-135">Vytvoření image Docker</span><span class="sxs-lookup"><span data-stu-id="8efcf-135">Create a Docker image</span></span>

<span data-ttu-id="8efcf-136">Image Docker je definovaná pomocí *souboru Dockerfile*, což je textový soubor, který obsahuje všechny příkazy potřebné k sestavení aplikace a instalaci všech závislostí, které jsou potřebné pro vytvoření nebo spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8efcf-136">A Docker image is defined by a *Dockerfile*, a text file that contains all the commands that are needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="8efcf-137">Následující příklad ukazuje nejjednodušší souboru Dockerfile pro aplikaci ASP.NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="8efcf-137">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="8efcf-138">Souboru Dockerfile má dvě části: první používá základní image `sdk` k sestavení a publikování aplikace. Druhá vytvoří bitovou kopii modulu runtime ze základu `aspnet`.</span><span class="sxs-lookup"><span data-stu-id="8efcf-138">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="8efcf-139">Důvodem je to, že bitová kopie `sdk` přibližně 900 MB v porovnání s přibližně 200 MB pro bitovou kopii modulu runtime a většina jejího obsahu není po dobu běhu potřebná.</span><span class="sxs-lookup"><span data-stu-id="8efcf-139">This is because the `sdk` image is around 900 MB compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="8efcf-140">Kroky sestavení</span><span class="sxs-lookup"><span data-stu-id="8efcf-140">The build steps</span></span>

| <span data-ttu-id="8efcf-141">Krok</span><span class="sxs-lookup"><span data-stu-id="8efcf-141">Step</span></span> | <span data-ttu-id="8efcf-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8efcf-142">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="8efcf-143">Deklaruje základní obrázek a přiřadí alias `builder` (vysvětlení naleznete v další části.)</span><span class="sxs-lookup"><span data-stu-id="8efcf-143">Declares the base image and assigns the `builder` alias (see next section for explanation).</span></span> |
| `WORKDIR /src` | <span data-ttu-id="8efcf-144">Vytvoří adresář `/src` a nastaví ho jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="8efcf-144">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="8efcf-145">Zkopíruje vše pod aktuálním adresářem v hostiteli do aktuálního adresáře v imagi.</span><span class="sxs-lookup"><span data-stu-id="8efcf-145">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="8efcf-146">Obnoví všechny externí balíčky (ASP.NET Core 3,0 Framework je předem nainstalovaná s SDK).</span><span class="sxs-lookup"><span data-stu-id="8efcf-146">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="8efcf-147">Vytvoří a publikuje sestavení pro vydání.</span><span class="sxs-lookup"><span data-stu-id="8efcf-147">Builds and publishes a Release build.</span></span> <span data-ttu-id="8efcf-148">Všimněte si, že příznak `--runtime` není povinný.</span><span class="sxs-lookup"><span data-stu-id="8efcf-148">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="8efcf-149">Kroky bitové kopie modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8efcf-149">The runtime image steps</span></span>

| <span data-ttu-id="8efcf-150">Krok</span><span class="sxs-lookup"><span data-stu-id="8efcf-150">Step</span></span> | <span data-ttu-id="8efcf-151">Popis</span><span class="sxs-lookup"><span data-stu-id="8efcf-151">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="8efcf-152">Deklaruje novou základní image.</span><span class="sxs-lookup"><span data-stu-id="8efcf-152">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="8efcf-153">Vytvoří adresář `/app` a nastaví ho jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="8efcf-153">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="8efcf-154">Zkopíruje publikovanou aplikaci z předchozího obrázku pomocí aliasu `builder` z prvního `FROM` řádku.</span><span class="sxs-lookup"><span data-stu-id="8efcf-154">Copies the published application from the previous image, using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="8efcf-155">Nastaví příkaz, který se spustí při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8efcf-155">Sets the command to run when the container starts.</span></span> <span data-ttu-id="8efcf-156">Příkaz `dotnet` v imagi modulu runtime může spouštět pouze soubory DLL.</span><span class="sxs-lookup"><span data-stu-id="8efcf-156">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="8efcf-157">HTTPS v Docker</span><span class="sxs-lookup"><span data-stu-id="8efcf-157">HTTPS in Docker</span></span>

<span data-ttu-id="8efcf-158">Základní image Microsoftu pro Docker nastaví proměnnou prostředí `ASPNETCORE_URLS` na `http://+:80`, což znamená, že Kestrel na tomto portu bude běžet bez protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8efcf-158">Microsoft's base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel will run without HTTPS on that port.</span></span> <span data-ttu-id="8efcf-159">Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [předchozí části](self-hosted.md)), měli byste ho přepsat nastavením proměnné prostředí **v části Vytvoření bitové kopie modulu runtime v rámci** vašeho souboru dockerfileu.</span><span class="sxs-lookup"><span data-stu-id="8efcf-159">If you're using HTTPS with a custom certificate (as described in [the previous section](self-hosted.md)), you should override this by setting the environment variable **in the runtime image creation part** of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="8efcf-160">Soubor. dockerignore</span><span class="sxs-lookup"><span data-stu-id="8efcf-160">The .dockerignore file</span></span>

<span data-ttu-id="8efcf-161">Podobně jako `.gitignore` soubory, které vyloučí určité soubory a adresáře ze správy zdrojového kódu, lze `.dockerignore` soubor použít k vyloučení souborů a adresářů, které se zkopírují do bitové kopie během sestavení.</span><span class="sxs-lookup"><span data-stu-id="8efcf-161">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="8efcf-162">To nejenom šetří čas kopírováním, ale může se taky vyhnout některým nematoucím chybám, které vznikají od sebe (zejména) `obj` Directory z počítače zkopírovaného do image.</span><span class="sxs-lookup"><span data-stu-id="8efcf-162">This not only saves time copying, but can also avoid some confusing errors that arise from having (particularly) the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="8efcf-163">Měli byste přidat alespoň položky pro `bin` a `obj` do souboru `.dockerignore`.</span><span class="sxs-lookup"><span data-stu-id="8efcf-163">You should add at least entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="8efcf-164">Sestavení image</span><span class="sxs-lookup"><span data-stu-id="8efcf-164">Build the image</span></span>

<span data-ttu-id="8efcf-165">Pro řešení s jednou aplikací, a proto jediným souboru Dockerfile, je nejjednodušší umístit souboru Dockerfile do základního adresáře. To znamená, že se jedná o stejný adresář jako soubor `.sln`.</span><span class="sxs-lookup"><span data-stu-id="8efcf-165">For a solution with a single application, and thus a single Dockerfile, it is simplest to put the Dockerfile in the base directory; that is, the same directory as the `.sln` file.</span></span> <span data-ttu-id="8efcf-166">V takovém případě pro sestavení image použijte následující příkaz `docker build` z adresáře obsahujícího rozhraní souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8efcf-166">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="8efcf-167">Nematoucí název `--tag` příznakem (který může být zkrácen na `-t`) určuje celý název obrázku, *včetně* skutečné značky, je-li tento parametr zadán.</span><span class="sxs-lookup"><span data-stu-id="8efcf-167">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, *including* the actual tag if specified.</span></span> <span data-ttu-id="8efcf-168">`.` na konci určuje *kontext* , ve kterém se bude sestavení spouštět; aktuální pracovní adresář pro příkazy `COPY` v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8efcf-168">The `.` at the end specifies the *context* in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="8efcf-169">Máte-li v rámci jednoho řešení více aplikací, můžete souboru Dockerfile pro každou aplikaci ve vlastní složce vedle `.csproj` souboru, ale přesto byste měli spustit příkaz `docker build` ze základního adresáře, aby bylo zajištěno, že řešení a všechny projekty jsou zkopírovány do obrázku.</span><span class="sxs-lookup"><span data-stu-id="8efcf-169">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file, but you should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="8efcf-170">Pomocí příznaku `--file` (nebo `-f`) můžete zadat souboru Dockerfile pod aktuálním adresářem.</span><span class="sxs-lookup"><span data-stu-id="8efcf-170">You can specify a Dockerfile below the current directory using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="8efcf-171">Spuštění image v kontejneru na počítači</span><span class="sxs-lookup"><span data-stu-id="8efcf-171">Run the image in a container on your machine</span></span>

<span data-ttu-id="8efcf-172">Pokud chcete spustit image v místní instanci Docker, použijte příkaz `docker run`.</span><span class="sxs-lookup"><span data-stu-id="8efcf-172">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="8efcf-173">Příznak `-ti` připojí aktuální terminál k terminálu kontejneru a spustí se v interaktivním režimu.</span><span class="sxs-lookup"><span data-stu-id="8efcf-173">The `-ti` flag connects your current terminal to the container's terminal and runs in interactive mode.</span></span> <span data-ttu-id="8efcf-174">`-p 5000:80` zveřejňuje (odkazy) port 80 na kontejneru na port 80 na síťovém rozhraní localhost.</span><span class="sxs-lookup"><span data-stu-id="8efcf-174">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="8efcf-175">Vložení image do registru</span><span class="sxs-lookup"><span data-stu-id="8efcf-175">Push the image to a registry</span></span>

<span data-ttu-id="8efcf-176">Jakmile ověříte, že bitová kopie funguje, budete ji muset odeslat do registru Docker, aby byla k dispozici v jiných systémech.</span><span class="sxs-lookup"><span data-stu-id="8efcf-176">Once you've verified that the image works, you need to push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="8efcf-177">Interní sítě budou muset zřídit registr Docker.</span><span class="sxs-lookup"><span data-stu-id="8efcf-177">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="8efcf-178">To může být jednoduché jako [`registry` image s vlastním prostředím Docker](https://docs.docker.com/registry/deploying/) (to je správné, registr Docker běží v kontejneru Docker), ale k dispozici jsou různá komplexnější řešení.</span><span class="sxs-lookup"><span data-stu-id="8efcf-178">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (that's right, the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="8efcf-179">Pro externí sdílení a cloudové použití jsou k dispozici různé spravované Registry, například [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="8efcf-179">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="8efcf-180">Pokud chcete přejít do dokovacího centra, pojmenujte název image názvem uživatele nebo organizace.</span><span class="sxs-lookup"><span data-stu-id="8efcf-180">To push to the Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="8efcf-181">Pokud chcete přejít do privátního registru, použijte předponu názvu bitové kopie s názvem hostitele registru a názvem organizace.</span><span class="sxs-lookup"><span data-stu-id="8efcf-181">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="8efcf-182">Jakmile je obrázek v registru, můžete ho nasadit na jednotlivé hostitele Docker nebo na modul pro orchestraci kontejnerů, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8efcf-182">Once the image is in a registry, you can deploy it to individual Docker hosts or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8efcf-183">[Předchozí](self-hosted.md)
>[Další](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="8efcf-183">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
