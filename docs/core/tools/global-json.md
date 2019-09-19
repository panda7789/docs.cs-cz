---
title: global.json – přehled
description: Naučte se používat soubor Global. JSON k nastavení verze .NET Core SDK při spouštění příkazů .NET Core CLI.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: 2c1fec102993b61e1eb699e8d3508b773302f569
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117430"
---
# <a name="globaljson-overview"></a><span data-ttu-id="bafa8-103">global.json – přehled</span><span class="sxs-lookup"><span data-stu-id="bafa8-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="bafa8-104">Soubor *Global. JSON* umožňuje definovat, která verze .NET Core SDK se používá při spuštění příkazů .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="bafa8-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="bafa8-105">Výběr .NET Core SDK je nezávislý na určení modulu runtime, který cílí na projekt.</span><span class="sxs-lookup"><span data-stu-id="bafa8-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="bafa8-106">Verze .NET Core SDK označuje, které verze .NET Core CLIch nástrojů se používají.</span><span class="sxs-lookup"><span data-stu-id="bafa8-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="bafa8-107">Obecně platí, že chcete použít nejnovější verzi nástrojů, takže není potřeba žádný soubor *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bafa8-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="bafa8-108">Další informace o určení modulu runtime místo toho naleznete v tématu [cílová rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="bafa8-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="bafa8-109">.NET Core SDK vyhledá soubor *Global. JSON* v aktuálním pracovním adresáři (to není nutně stejný jako adresář projektu) nebo v jednom z jeho nadřazených adresářů.</span><span class="sxs-lookup"><span data-stu-id="bafa8-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="bafa8-110">Global. JSON – schéma</span><span class="sxs-lookup"><span data-stu-id="bafa8-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="bafa8-111">sadě</span><span class="sxs-lookup"><span data-stu-id="bafa8-111">sdk</span></span>

<span data-ttu-id="bafa8-112">Zadejte: Objekt</span><span class="sxs-lookup"><span data-stu-id="bafa8-112">Type: Object</span></span>

<span data-ttu-id="bafa8-113">Určuje informace o .NET Core SDK k výběru.</span><span class="sxs-lookup"><span data-stu-id="bafa8-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="bafa8-114">verze</span><span class="sxs-lookup"><span data-stu-id="bafa8-114">version</span></span>

<span data-ttu-id="bafa8-115">Zadejte: String</span><span class="sxs-lookup"><span data-stu-id="bafa8-115">Type: String</span></span>

<span data-ttu-id="bafa8-116">Verze .NET Core SDK, která se má použít</span><span class="sxs-lookup"><span data-stu-id="bafa8-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="bafa8-117">Všimněte si, že toto pole:</span><span class="sxs-lookup"><span data-stu-id="bafa8-117">Note that this field:</span></span>

- <span data-ttu-id="bafa8-118">Nemá podporu pro expanzi, to znamená, že je nutné zadat úplné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="bafa8-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="bafa8-119">Nepodporuje rozsahy verzí.</span><span class="sxs-lookup"><span data-stu-id="bafa8-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="bafa8-120">Následující příklad ukazuje obsah souboru *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="bafa8-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="bafa8-121">Global. JSON a .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="bafa8-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="bafa8-122">Je užitečné znát, které verze jsou k dispozici, aby je bylo možné nastavit v *globálním souboru. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bafa8-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="bafa8-123">Úplný seznam podporovaných dostupných sad SDK najdete na stránce [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="bafa8-123">You can find the full list of supported available SDKs at the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span> <span data-ttu-id="bafa8-124">Počínaje sadou .NET Core 2,1 SDK můžete spuštěním následujícího příkazu ověřit, které verze sady SDK jsou na vašem počítači již nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="bafa8-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="bafa8-125">Pokud chcete na svém počítači nainstalovat další .NET Core SDK verze, navštivte stránku [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="bafa8-125">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="bafa8-126">Nový soubor *Global. JSON* můžete v aktuálním adresáři vytvořit spuštěním příkazu [dotnet New](dotnet-new.md) , podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bafa8-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="bafa8-127">Pravidla pro porovnání</span><span class="sxs-lookup"><span data-stu-id="bafa8-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="bafa8-128">Pravidla pro porovnání se řídí apphost, který je součástí modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bafa8-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="bafa8-129">K dispozici je nejnovější verze hostitele, pokud máte více nainstalovaných modulů runtime vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="bafa8-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="bafa8-130">Počínaje rozhraním .NET Core 2,0 se při určování používané verze sady SDK použijí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="bafa8-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="bafa8-131">Pokud nebyl nalezen soubor *Global. JSON* nebo soubor *Global. JSON* neurčuje verzi sady SDK, bude použita nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="bafa8-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="bafa8-132">Nejnovější verze sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS.</span><span class="sxs-lookup"><span data-stu-id="bafa8-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="bafa8-133">Pokud *Global. JSON* určí verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="bafa8-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="bafa8-134">Pokud je v počítači nalezena zadaná verze sady SDK, je použita tato přesná verze.</span><span class="sxs-lookup"><span data-stu-id="bafa8-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="bafa8-135">Pokud se zadaná verze sady SDK v tomto počítači nenajde, použije se nejnovější nainstalovaná **verze opravy** SDK této verze.</span><span class="sxs-lookup"><span data-stu-id="bafa8-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="bafa8-136">Nejnovější nainstalovaná **verze opravy** sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS.</span><span class="sxs-lookup"><span data-stu-id="bafa8-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="bafa8-137">V .NET Core 2,1 a novějších **verzích opravy** nižší, než je zadaná **verze opravy** , se v výběru sady SDK ignorují.</span><span class="sxs-lookup"><span data-stu-id="bafa8-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="bafa8-138">Pokud není nalezena zadaná verze sady SDK a příslušná **verze opravy** sady SDK, je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="bafa8-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="bafa8-139">Verze sady SDK se v současné době skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="bafa8-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="bafa8-140">**Verze .NET Core SDK funkce** je vyjádřena první číslicí (`x`) v poslední části čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="bafa8-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="bafa8-141">Obecně platí, že .NET Core SDK má rychlejší cyklus vydávání verzí než .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bafa8-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="bafa8-142">**Verze opravy** je definována posledními dvěma číslicemi (`yz`) v poslední části čísla (`xyz`) pro sadu SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="bafa8-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="bafa8-143">Pokud například zadáte `2.1.300` jako verzi sady SDK, výběr sady SDK vyhledá `2.1.399` , ale `2.1.400` nepovažuje se za verzi opravy `2.1.300`pro.</span><span class="sxs-lookup"><span data-stu-id="bafa8-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="bafa8-144">.NET Core SDK verze `2.1.100` prostřednictvím `2.1.201` byly vydány během přechodu mezi schématy čísel verzí `xyz` a nesprávně nezpracovávají zápis.</span><span class="sxs-lookup"><span data-stu-id="bafa8-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="bafa8-145">Důrazně doporučujeme, pokud zadáte tyto verze v souboru *Global. JSON* , abyste zajistili, že zadané verze jsou na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="bafa8-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="bafa8-146">Pokud jste v .NET Core SDK 1. x zadali verzi a nebyla nalezena žádná přesná shoda, použila se nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="bafa8-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="bafa8-147">Nejnovější verze sady SDK může být buď vydání verze, nebo předběžná verze – nejvyšší číslo verze služby WINS.</span><span class="sxs-lookup"><span data-stu-id="bafa8-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="bafa8-148">Řešení potíží s upozorněními sestavení</span><span class="sxs-lookup"><span data-stu-id="bafa8-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="bafa8-149">Pracujete s verzí Preview .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bafa8-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="bafa8-150">Verzi sady SDK můžete definovat prostřednictvím globálního souboru. JSON v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="bafa8-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="bafa8-151">Další informace<https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="bafa8-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="bafa8-152">Toto upozornění znamená, že projekt je kompilován pomocí verze Preview .NET Core SDK, jak je vysvětleno v části pravidla pro [porovnání](#matching-rules) .</span><span class="sxs-lookup"><span data-stu-id="bafa8-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="bafa8-153">Verze .NET Core SDK mají historii a závazek vysoké kvality.</span><span class="sxs-lookup"><span data-stu-id="bafa8-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="bafa8-154">Pokud ale nechcete používat verzi Preview, přidejte soubor *Global. JSON* do struktury hierarchie projektu, abyste určili, kterou verzi SDK chcete použít, a použijte `dotnet --list-sdks` k potvrzení, že je verze v počítači nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="bafa8-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="bafa8-155">Při vydání nové verze, pokud chcete použít novou verzi, odeberte soubor *Global. JSON* nebo ho aktualizujte tak, aby používal novější verzi.</span><span class="sxs-lookup"><span data-stu-id="bafa8-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="bafa8-156">Spouštěcí projekt {startupProject} cílí na rozhraní Framework. NETCoreApp verze {targetFrameworkVersion}.</span><span class="sxs-lookup"><span data-stu-id="bafa8-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="bafa8-157">Tato verze nástrojů příkazového řádku Entity Framework Core .NET podporuje pouze verzi 2,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="bafa8-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="bafa8-158">Informace o použití starších verzí nástrojů najdete v tématu.<https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="bafa8-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="bafa8-159">Počínaje sadou .NET Core 2,1 SDK (verze 2.1.300) `dotnet ef` se příkaz vloží do sady SDK.</span><span class="sxs-lookup"><span data-stu-id="bafa8-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="bafa8-160">Toto upozornění znamená, že projekt cílí na EF Core 1,0 nebo 1,1, což není kompatibilní s .NET Core 2,1 SDK a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="bafa8-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="bafa8-161">Chcete-li zkompilovat projekt, nainstalujte sadu .NET Core 2,0 SDK (verze 2.1.201) a dřívější na váš počítač a definujte požadovanou verzi sady SDK pomocí souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="bafa8-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="bafa8-162">Další informace o `dotnet ef` příkazu naleznete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="bafa8-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="bafa8-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bafa8-163">See also</span></span>

- [<span data-ttu-id="bafa8-164">Jak se řeší sady SDK projektu</span><span class="sxs-lookup"><span data-stu-id="bafa8-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
