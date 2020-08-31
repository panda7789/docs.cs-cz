---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602913"
---

[<span data-ttu-id="5ffad-101">Rozhraní .NET Core je dostupné z obchodu s modulem snap-in.</span><span class="sxs-lookup"><span data-stu-id="5ffad-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="5ffad-102">Modul snap je sada aplikací a její závislosti, které fungují beze změn v mnoha různých distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="5ffad-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="5ffad-103">Přichycení jsou zjistitelná a instalovatelné z úložiště pro modul snap-in.</span><span class="sxs-lookup"><span data-stu-id="5ffad-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="5ffad-104">Další informace o modulu snap-in najdete v tématu [Začínáme s modulem snap-in](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="5ffad-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="5ffad-105">Prostřednictvím modulu snap-in jsou k dispozici pouze podporované verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ffad-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="5ffad-106">Instalace sady SDK</span><span class="sxs-lookup"><span data-stu-id="5ffad-106">Install the SDK</span></span>

<span data-ttu-id="5ffad-107">Balíčky přichycení pro .NET Core SDK jsou všechny publikovány pod stejným identifikátorem: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="5ffad-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="5ffad-108">Konkrétní verzi sady SDK můžete nainstalovat zadáním kanálu.</span><span class="sxs-lookup"><span data-stu-id="5ffad-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="5ffad-109">Sada SDK obsahuje modul runtime pro přereakci.</span><span class="sxs-lookup"><span data-stu-id="5ffad-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="5ffad-110">V následující tabulce jsou uvedeny kanály:</span><span class="sxs-lookup"><span data-stu-id="5ffad-110">The following table list the channels:</span></span>

| <span data-ttu-id="5ffad-111">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ffad-111">.NET Core version</span></span> | <span data-ttu-id="5ffad-112">Přichycení balíčku</span><span class="sxs-lookup"><span data-stu-id="5ffad-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="5ffad-113">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5ffad-113">3.1 (LTS)</span></span>         | <span data-ttu-id="5ffad-114">`3.1` nebo `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="5ffad-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="5ffad-115">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5ffad-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="5ffad-116">.NET 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="5ffad-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="5ffad-117">`snap install`K instalaci balíčku .NET Core SDK přichycení použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ffad-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="5ffad-118">Pomocí `--channel` parametru určete, která verze se má nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="5ffad-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="5ffad-119">Pokud je tento parametr vynechán, `latest/stable` je použit.</span><span class="sxs-lookup"><span data-stu-id="5ffad-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="5ffad-120">V tomto příkladu `3.1` je určena:</span><span class="sxs-lookup"><span data-stu-id="5ffad-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="5ffad-121">Dále Zaregistrujte `dotnet` příkaz pro systém pomocí `snap alias` příkazu:</span><span class="sxs-lookup"><span data-stu-id="5ffad-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="5ffad-122">Tento příkaz je formátován jako: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="5ffad-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="5ffad-123">Můžete zvolit libovolný `{alias}` název, který chcete.</span><span class="sxs-lookup"><span data-stu-id="5ffad-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="5ffad-124">Příkaz můžete například pojmenovat po konkrétní verzi nainstalované modulem snap: `sudo snap alias dotnet-sdk.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="5ffad-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="5ffad-125">Při použití příkazu `dotnet31` vyvoláte tuto specifickou verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5ffad-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="5ffad-126">Není to ale kompatibilní s většinou výukových kurzů a příkladů, protože očekávají, že `dotnet` příkaz bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5ffad-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="5ffad-127">Instalace modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5ffad-127">Install the runtime</span></span>

<span data-ttu-id="5ffad-128">Balíčky přichycení pro modul runtime .NET Core jsou publikovány v rámci vlastního identifikátoru balíčku.</span><span class="sxs-lookup"><span data-stu-id="5ffad-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="5ffad-129">V následující tabulce jsou uvedeny identifikátory balíčků:</span><span class="sxs-lookup"><span data-stu-id="5ffad-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="5ffad-130">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ffad-130">.NET Core version</span></span> | <span data-ttu-id="5ffad-131">Přichycení balíčku</span><span class="sxs-lookup"><span data-stu-id="5ffad-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="5ffad-132">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5ffad-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="5ffad-133">3,0</span><span class="sxs-lookup"><span data-stu-id="5ffad-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="5ffad-134">2,2</span><span class="sxs-lookup"><span data-stu-id="5ffad-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="5ffad-135">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5ffad-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="5ffad-136">Použijte `snap install` příkaz k instalaci balíčku modulu runtime .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="5ffad-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="5ffad-137">V tomto příkladu je nainstalovaná platforma .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="5ffad-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="5ffad-138">Dále Zaregistrujte `dotnet` příkaz pro systém pomocí `snap alias` příkazu:</span><span class="sxs-lookup"><span data-stu-id="5ffad-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="5ffad-139">Tento příkaz je formátován jako: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="5ffad-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="5ffad-140">Můžete zvolit libovolný `{alias}` název, který chcete.</span><span class="sxs-lookup"><span data-stu-id="5ffad-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="5ffad-141">Příkaz můžete například pojmenovat po konkrétní verzi nainstalované modulem snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="5ffad-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="5ffad-142">Při použití příkazu `dotnet31` vyvoláte tuto specifickou verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5ffad-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="5ffad-143">Není to ale kompatibilní s většinou výukových kurzů a příkladů, protože očekávají, že `dotnet` příkaz bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5ffad-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="5ffad-144">Chyby certifikátu SSL</span><span class="sxs-lookup"><span data-stu-id="5ffad-144">SSL Certificate errors</span></span>

<span data-ttu-id="5ffad-145">Když je rozhraní .NET nainstalované prostřednictvím modulu snap-in, je možné, že na některých distribuce se certifikáty .NET SSL nenašly a v průběhu této chyby se může zobrazit chyba podobná této `restore` :</span><span class="sxs-lookup"><span data-stu-id="5ffad-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="5ffad-146">Chcete-li tento problém vyřešit, nastavte několik proměnných prostředí:</span><span class="sxs-lookup"><span data-stu-id="5ffad-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="5ffad-147">Umístění certifikátu se bude lišit podle distribuce.</span><span class="sxs-lookup"><span data-stu-id="5ffad-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="5ffad-148">Tady jsou umístění pro distribuce, kde jsme narazili na problém.</span><span class="sxs-lookup"><span data-stu-id="5ffad-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="5ffad-149">Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="5ffad-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="5ffad-150">OpenSUSE `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="5ffad-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="5ffad-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="5ffad-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
