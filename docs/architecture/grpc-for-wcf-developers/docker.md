---
title: Docker - gRPC pro vývojáře WCF
description: Vytváření imitací Dockeru pro ASP.NET core gRPC aplikace
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148111"
---
# <a name="create-docker-images"></a><span data-ttu-id="c309c-103">Vytváření imitek Dockeru</span><span class="sxs-lookup"><span data-stu-id="c309c-103">Create Docker images</span></span>

<span data-ttu-id="c309c-104">Tato část popisuje vytváření imitek Dockeru pro ASP.NET core gRPC aplikace, připravené ke spuštění v Dockeru, Kubernetes nebo jiných kontejnerových prostředích.</span><span class="sxs-lookup"><span data-stu-id="c309c-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="c309c-105">Použitá ukázková aplikace s ASP.NET webové aplikace Core MVC a službou gRPC je k dispozici v úložišti [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c309c-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="c309c-106">Základní image Microsoftu pro aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c309c-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="c309c-107">Společnost Microsoft poskytuje řadu základních bitových kopií pro vytváření a spouštění aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c309c-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="c309c-108">Chcete-li vytvořit obraz ASP.NET Jádra 3.0, použijte dva základní obrazy:</span><span class="sxs-lookup"><span data-stu-id="c309c-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="c309c-109">Bitovou kopii sady SDK pro sestavení a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="c309c-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="c309c-110">Bitová kopie za běhu pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="c309c-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="c309c-111">Image</span><span class="sxs-lookup"><span data-stu-id="c309c-111">Image</span></span> | <span data-ttu-id="c309c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c309c-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="c309c-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="c309c-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="c309c-114">Pro vytváření `docker build`aplikací s .</span><span class="sxs-lookup"><span data-stu-id="c309c-114">For building applications with `docker build`.</span></span> <span data-ttu-id="c309c-115">Nepoužívat ve výrobě.</span><span class="sxs-lookup"><span data-stu-id="c309c-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="c309c-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="c309c-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="c309c-117">Obsahuje závislosti runtime a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c309c-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="c309c-118">Pro výrobu.</span><span class="sxs-lookup"><span data-stu-id="c309c-118">For production.</span></span> |

<span data-ttu-id="c309c-119">Pro každý obrázek existují čtyři varianty založené na různých distribucích Linuxu, které se vyznačují značkami.</span><span class="sxs-lookup"><span data-stu-id="c309c-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="c309c-120">Značka obrázku (značky)</span><span class="sxs-lookup"><span data-stu-id="c309c-120">Image tag(s)</span></span> | <span data-ttu-id="c309c-121">Linux</span><span class="sxs-lookup"><span data-stu-id="c309c-121">Linux</span></span> | <span data-ttu-id="c309c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c309c-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="c309c-123">3.0-buster, 3.0</span><span class="sxs-lookup"><span data-stu-id="c309c-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="c309c-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="c309c-124">Debian 10</span></span> | <span data-ttu-id="c309c-125">Výchozí obrázek, pokud není zadána žádná varianta operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c309c-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="c309c-126">3.0-alpské</span><span class="sxs-lookup"><span data-stu-id="c309c-126">3.0-alpine</span></span> | <span data-ttu-id="c309c-127">Alpská 3,9</span><span class="sxs-lookup"><span data-stu-id="c309c-127">Alpine 3.9</span></span> | <span data-ttu-id="c309c-128">Alpské základní obrazy jsou mnohem menší než ty Debian nebo Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c309c-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="c309c-129">3.0-diskotéka</span><span class="sxs-lookup"><span data-stu-id="c309c-129">3.0-disco</span></span> | <span data-ttu-id="c309c-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="c309c-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="c309c-131">3.0-bionické</span><span class="sxs-lookup"><span data-stu-id="c309c-131">3.0-bionic</span></span> | <span data-ttu-id="c309c-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c309c-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="c309c-133">Základní obrázek Alpine je kolem 100 MB, ve srovnání s 200 MB pro obrazy Debian a Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c309c-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="c309c-134">Některé softwarové balíčky nebo knihovny nemusí být ve správě balíčků společnosti Alpine k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c309c-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="c309c-135">Pokud si nejste jisti, který obrázek použít, měli byste pravděpodobně zvolit výchozí Debian.</span><span class="sxs-lookup"><span data-stu-id="c309c-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c309c-136">Ujistěte se, že používáte stejnou variantu Linuxu pro sestavení a runtime.</span><span class="sxs-lookup"><span data-stu-id="c309c-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="c309c-137">Aplikace vytvořené a publikované na jedné variantě nemusí fungovat na jiné variantě.</span><span class="sxs-lookup"><span data-stu-id="c309c-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="c309c-138">Vytvoření image Dockeru</span><span class="sxs-lookup"><span data-stu-id="c309c-138">Create a Docker image</span></span>

<span data-ttu-id="c309c-139">Image Dockeru je definována *dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="c309c-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="c309c-140">Jedná se o textový soubor, který obsahuje všechny příkazy potřebné k vytvoření aplikace a instalaci všech závislostí, které jsou požadovány pro sestavení nebo spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c309c-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="c309c-141">Následující příklad ukazuje nejjednodušší Dockerfile pro ASP.NET core 3.0 aplikace:</span><span class="sxs-lookup"><span data-stu-id="c309c-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="c309c-142">Dockerfile má dvě části: první `sdk` používá základní image k sestavení a publikování aplikace; druhý vytvoří bitovou kopii `aspnet` za běhu ze základny.</span><span class="sxs-lookup"><span data-stu-id="c309c-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="c309c-143">Důvodem je, že `sdk` obraz je kolem 900 MB, ve srovnání s přibližně 200 MB pro bitovou kopii za běhu a většina jeho obsahu jsou zbytečné za běhu.</span><span class="sxs-lookup"><span data-stu-id="c309c-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="c309c-144">Kroky sestavení</span><span class="sxs-lookup"><span data-stu-id="c309c-144">The build steps</span></span>

| <span data-ttu-id="c309c-145">Krok</span><span class="sxs-lookup"><span data-stu-id="c309c-145">Step</span></span> | <span data-ttu-id="c309c-146">Popis</span><span class="sxs-lookup"><span data-stu-id="c309c-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c309c-147">Deklaruje základní obrázek a přiřadí `builder` alias.</span><span class="sxs-lookup"><span data-stu-id="c309c-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="c309c-148">Vytvoří `/src` adresář a nastaví jej jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="c309c-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="c309c-149">Zkopíruje vše pod aktuálním adresářem na hostiteli do aktuálního adresáře v obraze.</span><span class="sxs-lookup"><span data-stu-id="c309c-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="c309c-150">Obnoví všechny externí balíčky (ASP.NET core 3.0 framework je předinstalovaný s SadsDK).</span><span class="sxs-lookup"><span data-stu-id="c309c-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="c309c-151">Vytvoří a publikuje sestavení verze.</span><span class="sxs-lookup"><span data-stu-id="c309c-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="c309c-152">Všimněte `--runtime` si, že příznak není povinný.</span><span class="sxs-lookup"><span data-stu-id="c309c-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="c309c-153">Kroky bitové kopie za běhu</span><span class="sxs-lookup"><span data-stu-id="c309c-153">The runtime image steps</span></span>

| <span data-ttu-id="c309c-154">Krok</span><span class="sxs-lookup"><span data-stu-id="c309c-154">Step</span></span> | <span data-ttu-id="c309c-155">Popis</span><span class="sxs-lookup"><span data-stu-id="c309c-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="c309c-156">Deklaruje novou základní bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c309c-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="c309c-157">Vytvoří `/app` adresář a nastaví jej jako aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="c309c-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="c309c-158">Zkopíruje publikovanou aplikaci z předchozího `builder` obrázku `FROM` pomocí aliasu z prvního řádku.</span><span class="sxs-lookup"><span data-stu-id="c309c-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="c309c-159">Nastaví spuštění příkazu při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c309c-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="c309c-160">Příkaz `dotnet` v bitové kopii za běhu může spouštět pouze soubory DLL.</span><span class="sxs-lookup"><span data-stu-id="c309c-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="c309c-161">HTTPS v Dockeru</span><span class="sxs-lookup"><span data-stu-id="c309c-161">HTTPS in Docker</span></span>

<span data-ttu-id="c309c-162">Základní image Microsoftu `ASPNETCORE_URLS` pro Docker `http://+:80`nastavují proměnnou prostředí na , což znamená, že Kestrel běží na tomto portu bez protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c309c-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="c309c-163">Pokud používáte protokol HTTPS s vlastním certifikátem (jak je popsáno v [aplikacích gRPC s vlastním hostitelem),](self-hosted.md)měli byste to přepsat.</span><span class="sxs-lookup"><span data-stu-id="c309c-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="c309c-164">Nastavte proměnnou prostředí v části vytvoření bitové kopie za běhu vašeho dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c309c-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="c309c-165">Soubor .dockerignore</span><span class="sxs-lookup"><span data-stu-id="c309c-165">The .dockerignore file</span></span>

<span data-ttu-id="c309c-166">Podobně `.gitignore` jako soubory, které vylučují `.dockerignore` určité soubory a adresáře ze správy zdrojového kódu, lze soubor použít k vyloučení souborů a adresářů z kopírování do bitové kopie během sestavení.</span><span class="sxs-lookup"><span data-stu-id="c309c-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="c309c-167">To nejen šetří čas kopírování, ale může také zabránit některým `obj` chybám, které vznikají z toho, že adresář z počítače zkopírován do obrazu.</span><span class="sxs-lookup"><span data-stu-id="c309c-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="c309c-168">Minimálně byste měli přidat `bin` položky pro a `obj` do `.dockerignore` souboru.</span><span class="sxs-lookup"><span data-stu-id="c309c-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="c309c-169">Sestavení image</span><span class="sxs-lookup"><span data-stu-id="c309c-169">Build the image</span></span>

<span data-ttu-id="c309c-170">Pro řešení s jedinou aplikací, a tedy jeden Dockerfile, je nejjednodušší umístit Dockerfile v základním adresáři.</span><span class="sxs-lookup"><span data-stu-id="c309c-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="c309c-171">Jinými slovy, vložte jej do `.sln` stejného adresáře jako soubor.</span><span class="sxs-lookup"><span data-stu-id="c309c-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="c309c-172">V takovém případě k vytvoření bitové `docker build` kopie použijte následující příkaz z adresáře obsahujícího soubor Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c309c-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="c309c-173">Zmateně pojmenovaný `--tag` příznak (který lze `-t`zkrátit na ) určuje celý název obrázku, včetně skutečné značky, pokud je zadána.</span><span class="sxs-lookup"><span data-stu-id="c309c-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="c309c-174">Na `.` konci určuje kontext, ve kterém bude spuštěno sestavení; aktuální pracovní adresář `COPY` pro příkazy v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c309c-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="c309c-175">Pokud máte více aplikací v rámci jednoho řešení, můžete zachovat Dockerfile pro `.csproj` každou aplikaci ve své vlastní složce, vedle souboru.</span><span class="sxs-lookup"><span data-stu-id="c309c-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="c309c-176">Stále byste měli `docker build` spustit příkaz ze základního adresáře, abyste zajistili, že řešení a všechny projekty jsou zkopírovány do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c309c-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="c309c-177">Soubor Dockerfile můžete zadat pod aktuálním `--file` adresářem pomocí příznaku (nebo). `-f`</span><span class="sxs-lookup"><span data-stu-id="c309c-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="c309c-178">Spuštění obrázku v kontejneru na počítači</span><span class="sxs-lookup"><span data-stu-id="c309c-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="c309c-179">Chcete-li spustit bitovou kopii `docker run` v místní instanci Dockeru, použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c309c-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="c309c-180">Příznak `-ti` připojí aktuální terminál k terminálu kontejneru a běží v interaktivním režimu.</span><span class="sxs-lookup"><span data-stu-id="c309c-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="c309c-181">Publikuje `-p 5000:80` (odkazy) port 80 na kontejneru port 5000 na localhost síťové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c309c-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="c309c-182">Zasunutí bitové kopie do registru</span><span class="sxs-lookup"><span data-stu-id="c309c-182">Push the image to a registry</span></span>

<span data-ttu-id="c309c-183">Po ověření, že image funguje, zatlačte ji do registru Dockeru, aby byla k dispozici v jiných systémech.</span><span class="sxs-lookup"><span data-stu-id="c309c-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="c309c-184">Interní sítě budou muset zřídit registr Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c309c-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="c309c-185">To může být stejně jednoduché jako spuštění [vlastní `registry` image Dockeru](https://docs.docker.com/registry/deploying/) (registr Dockeru běží v kontejneru Dockeru), ale jsou k dispozici různá komplexnější řešení.</span><span class="sxs-lookup"><span data-stu-id="c309c-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="c309c-186">Pro externí sdílení a využití cloudu jsou k dispozici různé spravované registry, jako je [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) nebo Docker [Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="c309c-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="c309c-187">Chcete-li přetlačit do Centra Dockeru, předponu název bitové kopie s názvem uživatele nebo organizace.</span><span class="sxs-lookup"><span data-stu-id="c309c-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="c309c-188">Chcete-li přetlačit do soukromého registru, předponu název bitové kopie s názvem hostitele registru a názvem organizace.</span><span class="sxs-lookup"><span data-stu-id="c309c-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="c309c-189">Poté, co je bitová kopie v registru, můžete ji nasadit na jednotlivé hostitele Dockeru nebo do modulu orchestrace kontejnerů, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c309c-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c309c-190">[Předchozí](self-hosted.md)
>[další](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="c309c-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
