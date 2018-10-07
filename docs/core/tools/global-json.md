---
title: Přehled Global.JSON
description: Zjistěte, jak použít soubor global.json se nastavit verzi .NET Core SDK, při spuštění příkazů rozhraní příkazového řádku .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 07/30/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 05ec296c4c8210c63c7c1b5ce63ef598ca6ac719
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838075"
---
# <a name="globaljson-overview"></a><span data-ttu-id="ad379-103">Přehled Global.JSON</span><span class="sxs-lookup"><span data-stu-id="ad379-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="ad379-104">*Global.json* souboru můžete zadat, která verze rozhraní .NET Core SDK se používá při spuštění příkazů rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad379-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="ad379-105">Výběr sady .NET Core SDK je nezávislý na určení modulu runtime váš projekt cílí.</span><span class="sxs-lookup"><span data-stu-id="ad379-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="ad379-106">.NET Core SDK verze označuje, které verze nástroje .NET Core CLI používají.</span><span class="sxs-lookup"><span data-stu-id="ad379-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="ad379-107">Obecně platí, kterou chcete použít nejnovější verzi nástrojů, proto není *global.json* soubor nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="ad379-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="ad379-108">Další informace o zadávání místo toho modul runtime, naleznete v tématu [platforem](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ad379-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="ad379-109">Sada .NET core SDK hledá *global.json* soubor v aktuálním pracovním adresáři (který není nutně stejné jako adresář projektu) nebo v některém z jeho nadřazené adresáře.</span><span class="sxs-lookup"><span data-stu-id="ad379-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="ad379-110">Global.JSON schématu</span><span class="sxs-lookup"><span data-stu-id="ad379-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="ad379-111">Sady SDK</span><span class="sxs-lookup"><span data-stu-id="ad379-111">sdk</span></span>

<span data-ttu-id="ad379-112">Typ: objekt</span><span class="sxs-lookup"><span data-stu-id="ad379-112">Type: Object</span></span>

<span data-ttu-id="ad379-113">Určuje informace o .NET Core SDK k výběru.</span><span class="sxs-lookup"><span data-stu-id="ad379-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="ad379-114">verze</span><span class="sxs-lookup"><span data-stu-id="ad379-114">version</span></span>

<span data-ttu-id="ad379-115">Typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ad379-115">Type: String</span></span>

<span data-ttu-id="ad379-116">Verze .NET Core SDK používat.</span><span class="sxs-lookup"><span data-stu-id="ad379-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="ad379-117">Všimněte si, že toto pole:</span><span class="sxs-lookup"><span data-stu-id="ad379-117">Note that this field:</span></span>

- <span data-ttu-id="ad379-118">Nebude mít podporu podpory zástupných znaků, to znamená, celé číslo verze musí být zadaný.</span><span class="sxs-lookup"><span data-stu-id="ad379-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="ad379-119">Nepodporuje rozsahů verzí.</span><span class="sxs-lookup"><span data-stu-id="ad379-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="ad379-120">Následující příklad ukazuje obsah *global.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="ad379-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.1.300"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="ad379-121">Global.JSON a .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="ad379-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="ad379-122">Je užitečné vědět, jaké verze jsou k dispozici, aby bylo možné nastavit jednu *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="ad379-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="ad379-123">Najdete úplný seznam podporovaných sad SDK k dispozici na [.NET stáhne](https://www.microsoft.com/net/download/all) lokality.</span><span class="sxs-lookup"><span data-stu-id="ad379-123">You can find the full list of supported available SDKs at the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span> <span data-ttu-id="ad379-124">Spouští se sadou .NET Core SDK 2.1, můžete spustit následující příkaz k ověření, které verze sady SDK jsou již nainstalovány na vašem počítači:</span><span class="sxs-lookup"><span data-stu-id="ad379-124">Starting with .NET Core SDK 2.1, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```console
dotnet --list-sdks
```

<span data-ttu-id="ad379-125">Pokud chcete nainstalovat další verze sady SDK .NET Core na počítači, přejděte [.NET stáhne](https://www.microsoft.com/net/download/all) lokality.</span><span class="sxs-lookup"><span data-stu-id="ad379-125">To install additional .NET Core SDK versions on your machine, visit the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span>

<span data-ttu-id="ad379-126">Můžete vytvořit nový *global.json* soubor v aktuálním adresáři pomocí provádí [dotnet nové](dotnet-new.md) příkazu, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ad379-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```console
dotnet new globaljson --sdk-version 2.1.300
```

## <a name="matching-rules"></a><span data-ttu-id="ad379-127">Odpovídající pravidla</span><span class="sxs-lookup"><span data-stu-id="ad379-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="ad379-128">Pravidla pro porovnávání se řídí apphost, který je součástí modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad379-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="ad379-129">Pokud máte více modulů runtime nainstalovaný – souběžně se používá nejnovější verzi hostitele.</span><span class="sxs-lookup"><span data-stu-id="ad379-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="ad379-130">Od verze rozhraní .NET Core 2.0, platí následující pravidla při určování, kterou verzi sady SDK používat:</span><span class="sxs-lookup"><span data-stu-id="ad379-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="ad379-131">Pokud ne *global.json* nalezen soubor nebo *global.json* nemá určenou verzi sady SDK se používá nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ad379-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="ad379-132">Nejnovější verze sady SDK může být verze nebo předběžné verze-wins nejvyšší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ad379-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="ad379-133">Pokud *global.json* specifikovat verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="ad379-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="ad379-134">Pokud zadaná verze SDK je nalezen na počítači, použije se tento přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="ad379-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="ad379-135">Pokud zadaná verze SDK nebyl nalezen na počítači, nainstaluje nejnovější SDK **verzi opravy** , který je použita verze.</span><span class="sxs-lookup"><span data-stu-id="ad379-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="ad379-136">Nainstalovat nejnovější verzi sady SDK **verzi opravy** může být verze nebo předběžné verze nejvyšší číslo wins.</span><span class="sxs-lookup"><span data-stu-id="ad379-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="ad379-137">V rozhraní .NET Core 2.1 a vyšší **oprava verze** nižší než **verzi opravy** zadané jsou ignorovány ve výběru sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ad379-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="ad379-138">Pokud zadaná verze sady SDK a vhodnou sadu SDK **verzi opravy** nebyl nalezen, je vržena chyba.</span><span class="sxs-lookup"><span data-stu-id="ad379-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="ad379-139">Verze sady SDK se aktuálně skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="ad379-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="ad379-140">**Funkce uvolnění** sady .NET Core SDK je reprezentována první číslice (`x`) v poslední část čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="ad379-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="ad379-141">Obecně platí .NET Core SDK má rychlejší cyklu vydávání verzí, než .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad379-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="ad379-142">**Verzi opravy** je definován posledních dvou číslic (`yz`) v poslední část čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="ad379-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="ad379-143">Pokud zadáte například `2.1.300` jako verzi sady SDK, vyhledá SDK výběr až `2.1.399` ale `2.1.400` není považováno za verzi opravy pro `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="ad379-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="ad379-144">Sada .NET core SDK verze `2.1.100` prostřednictvím `2.1.201` vydané během přechodu mezi schémata číslo verze a nezpracovávají správně `xyz` zápis.</span><span class="sxs-lookup"><span data-stu-id="ad379-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="ad379-145">Důrazně doporučujeme, pokud zadáte tyto verze v *global.json* souboru, který je zajistit, že jsou zadané verze na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="ad379-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="ad379-146">S .NET Core SDK byl nalezen 1.x, pokud jste zadali, verzi a přesná shoda není, byl použit nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ad379-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="ad379-147">Nejnovější verze sady SDK může být verze nebo předběžné verze-wins nejvyšší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="ad379-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="ad379-148">Řešení potíží s upozorněními sestavení</span><span class="sxs-lookup"><span data-stu-id="ad379-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="ad379-149">Pracujete s předběžnou verzi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ad379-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="ad379-150">Verze sady SDK prostřednictvím souboru global.json můžete definovat v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="ad379-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="ad379-151">Informace najdete na <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="ad379-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="ad379-152">Toto upozornění signalizuje, že váš projekt se kompiluje ve verzi preview sady .NET Core SDK, jak je vysvětleno v [pravidel](#matching-rules) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ad379-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="ad379-153">Verze .NET core SDK mají historie a bez závazků toho, že vysoce kvalitní.</span><span class="sxs-lookup"><span data-stu-id="ad379-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="ad379-154">Nicméně, pokud už nechcete používat verzi preview, přidejte *global.json* soubor struktuře hierarchie projektu zadat verzi sady SDK, která se má použít a použijte `dotnet --list-sdks` potvrďte, že na svém počítači je nainstalována verze.</span><span class="sxs-lookup"><span data-stu-id="ad379-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="ad379-155">Po vydání nové verze, na použití nové verze, buď odeberte *global.json* souboru nebo ji chcete používat novější verzi.</span><span class="sxs-lookup"><span data-stu-id="ad379-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="ad379-156">Při spuštění projektu "{výchozí projekt}" cíleného na rozhraní framework '. NETCoreApp' verze {targetFrameworkVersion}.</span><span class="sxs-lookup"><span data-stu-id="ad379-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="ad379-157">Tato verze nástroje příkazového řádku .NET Core Entity Framework podporuje pouze verze 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="ad379-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="ad379-158">Informace o používání starší verze nástrojů najdete v tématu <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="ad379-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="ad379-159">Spouští se sadou .NET Core SDK 2.1 (vs.</span><span class="sxs-lookup"><span data-stu-id="ad379-159">Starting with .NET Core SDK 2.1 (v.</span></span> <span data-ttu-id="ad379-160">2.1.300) `dotnet ef` příkaz je zahrnutý v sadě SDK.</span><span class="sxs-lookup"><span data-stu-id="ad379-160">2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="ad379-161">Toto upozornění signalizuje, že váš projekt cílí na EF Core 1.0 a 1.1, který není kompatibilní s .NET Core SDK 2.1 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="ad379-161">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core SDK 2.1 and later versions.</span></span> <span data-ttu-id="ad379-162">Chcete-li zkompilovat váš projekt, nainstalujte .NET Core SDK 2.0 (vs.</span><span class="sxs-lookup"><span data-stu-id="ad379-162">To compile your project, install .NET Core SDK 2.0 (v.</span></span> <span data-ttu-id="ad379-163">2.1.201) a starších na vašem počítači a definovat požadovanou verzi sady SDK pomocí *global.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="ad379-163">2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="ad379-164">Další informace o `dotnet ef` naleznete [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="ad379-164">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad379-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad379-165">See also</span></span>

* [<span data-ttu-id="ad379-166">Způsob řešení projekt sady SDK</span><span class="sxs-lookup"><span data-stu-id="ad379-166">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
