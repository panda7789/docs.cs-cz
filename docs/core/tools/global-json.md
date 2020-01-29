---
title: global.json – přehled
description: Naučte se používat soubor Global. JSON k nastavení verze .NET Core SDK při spouštění příkazů .NET Core CLI.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f02c9129a707ddddb2c5e1975b75cc35abc5cd55
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733975"
---
# <a name="globaljson-overview"></a><span data-ttu-id="15045-103">global.json – přehled</span><span class="sxs-lookup"><span data-stu-id="15045-103">global.json overview</span></span>

<span data-ttu-id="15045-104">**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="15045-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="15045-105">Soubor *Global. JSON* umožňuje definovat, která verze .NET Core SDK se používá při spuštění příkazů .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="15045-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="15045-106">Výběr .NET Core SDK je nezávislý na určení modulu runtime, který cílí na projekt.</span><span class="sxs-lookup"><span data-stu-id="15045-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="15045-107">Verze .NET Core SDK označuje, které verze .NET Core CLIch nástrojů se používají.</span><span class="sxs-lookup"><span data-stu-id="15045-107">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span>

<span data-ttu-id="15045-108">Obecně platí, že chcete použít nejnovější verzi nástrojů SDK, takže není potřeba žádný soubor *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="15045-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="15045-109">V některých pokročilých scénářích můžete chtít řídit verzi nástrojů sady SDK a tento článek vysvětluje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="15045-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="15045-110">Další informace o určení modulu runtime místo toho naleznete v tématu [cílová rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="15045-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="15045-111">.NET Core SDK vyhledá soubor *Global. JSON* v aktuálním pracovním adresáři (to není nutně stejný jako adresář projektu) nebo v jednom z jeho nadřazených adresářů.</span><span class="sxs-lookup"><span data-stu-id="15045-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="15045-112">Global. JSON – schéma</span><span class="sxs-lookup"><span data-stu-id="15045-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="15045-113">sdk</span><span class="sxs-lookup"><span data-stu-id="15045-113">sdk</span></span>

<span data-ttu-id="15045-114">Zadejte: `object`</span><span class="sxs-lookup"><span data-stu-id="15045-114">Type: `object`</span></span>

<span data-ttu-id="15045-115">Určuje informace o .NET Core SDK k výběru.</span><span class="sxs-lookup"><span data-stu-id="15045-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="15045-116">Verze nástroje</span><span class="sxs-lookup"><span data-stu-id="15045-116">version</span></span>

- <span data-ttu-id="15045-117">Zadejte: `string`</span><span class="sxs-lookup"><span data-stu-id="15045-117">Type: `string`</span></span>

- <span data-ttu-id="15045-118">Dostupné od verze: .NET Core 1,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="15045-119">Verze .NET Core SDK, která se má použít</span><span class="sxs-lookup"><span data-stu-id="15045-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="15045-120">Toto pole:</span><span class="sxs-lookup"><span data-stu-id="15045-120">This field:</span></span>

- <span data-ttu-id="15045-121">Nemá podporu zástupných znaků, to znamená, že je nutné zadat úplné číslo verze.</span><span class="sxs-lookup"><span data-stu-id="15045-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="15045-122">Nepodporuje rozsahy verzí.</span><span class="sxs-lookup"><span data-stu-id="15045-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="15045-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="15045-123">allowPrerelease</span></span>

- <span data-ttu-id="15045-124">Zadejte: `boolean`</span><span class="sxs-lookup"><span data-stu-id="15045-124">Type: `boolean`</span></span>

- <span data-ttu-id="15045-125">Dostupné od verze: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="15045-126">Určuje, zda má Řešitel sady SDK zvážit předprodejní verze při výběru verze sady SDK, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="15045-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="15045-127">Pokud tuto hodnotu nenastavíte explicitně, bude výchozí hodnota záviset na tom, jestli spouštíte ze sady Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="15045-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="15045-128">Pokud nejste **v aplikaci** Visual Studio, výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="15045-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="15045-129">Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze.</span><span class="sxs-lookup"><span data-stu-id="15045-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="15045-130">To znamená, že pokud používáte verzi Preview sady Visual Studio nebo jste nastavili náhledy **použití možnosti .NET Core SDK** (v části **nástroje** > **Možnosti** \*\* >  > \*\* funkce ve **verzi Preview**), výchozí hodnota je `true`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="15045-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="15045-131">Dopředné obnovení</span><span class="sxs-lookup"><span data-stu-id="15045-131">rollForward</span></span>

- <span data-ttu-id="15045-132">Zadejte: `string`</span><span class="sxs-lookup"><span data-stu-id="15045-132">Type: `string`</span></span>

- <span data-ttu-id="15045-133">Dostupné od verze: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="15045-134">Zásada pro převzetí služeb při obnovení, která se má použít při výběru verze sady SDK, a to buď jako záložní, pokud konkrétní verze sady SDK chybí, nebo jako direktiva pro použití vyšší verze.</span><span class="sxs-lookup"><span data-stu-id="15045-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="15045-135">Pokud nenastavujete `latestMajor`, je nutné zadat [verzi](#version) s `rollForward` hodnotou.</span><span class="sxs-lookup"><span data-stu-id="15045-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="15045-136">Pro pochopení dostupných zásad a jejich chování zvažte následující definice verze sady SDK ve formátu `x.y.znn`:</span><span class="sxs-lookup"><span data-stu-id="15045-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="15045-137">`x` je hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="15045-137">`x` is the major version.</span></span>
- <span data-ttu-id="15045-138">`y` je vedlejší verze.</span><span class="sxs-lookup"><span data-stu-id="15045-138">`y` is the minor version.</span></span>
- <span data-ttu-id="15045-139">`z` je pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-139">`z` is the feature band.</span></span>
- <span data-ttu-id="15045-140">`nn` je verze opravy.</span><span class="sxs-lookup"><span data-stu-id="15045-140">`nn` is the patch version.</span></span>

<span data-ttu-id="15045-141">Následující tabulka uvádí možné hodnoty pro `rollForward` klíč:</span><span class="sxs-lookup"><span data-stu-id="15045-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="15045-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="15045-142">Value</span></span>         | <span data-ttu-id="15045-143">Chování</span><span class="sxs-lookup"><span data-stu-id="15045-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="15045-144">Používá zadanou verzi.</span><span class="sxs-lookup"><span data-stu-id="15045-144">Uses the specified version.</span></span> <br> <span data-ttu-id="15045-145">Pokud se nenajde, vrátí se k nejnovější úrovni oprav.</span><span class="sxs-lookup"><span data-stu-id="15045-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="15045-146">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="15045-147">Tato hodnota je starší verze chování z dřívějších verzí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="15045-148">Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="15045-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="15045-149">Pokud se nenajde, vrátí se k nejbližšímu novému pásma funkce v rámci stejné hlavní nebo dílčí funkce a použije nejnovější úroveň opravy pro daný panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-150">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="15045-151">Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="15045-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="15045-152">Pokud se nenajde, vrátí se k nejbližšímu pásmu funkce v rámci stejné hlavní nebo dílčí verze a použije se nejnovější úroveň opravy pro tento panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-153">Pokud se nenalezne, vrátí se k nejbližšímu vyššímu menšímu množství a rozstupnému pásma funkcí v rámci stejné hlavní úrovně a použije se nejnovější úroveň opravy pro daný panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-154">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="15045-155">Používá nejnovější úroveň opravy pro zadaný hlavní, vedlejší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="15045-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="15045-156">Pokud se nenajde, vrátí se k nejbližšímu pásmu funkce v rámci stejné hlavní nebo dílčí verze a použije se nejnovější úroveň opravy pro tento panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-157">Pokud se nenalezne, vrátí se k nejbližšímu vyššímu menšímu množství a rozstupnému pásma funkcí v rámci stejné hlavní úrovně a použije se nejnovější úroveň opravy pro daný panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-158">Pokud se nenalezne, vrátí se k nejbližšímu většímu hornímu, vedlejšímu a funkčnímu pásmu a použije se nejnovější úroveň opravy pro daný panel funkcí.</span><span class="sxs-lookup"><span data-stu-id="15045-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="15045-159">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="15045-160">Používá nejnovější nainstalovanou úroveň opravy, která odpovídá požadovanému hlavnímu, vedlejšímu a funkčnímu pásmu funkce s úrovní oprav a která je větší nebo rovna zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="15045-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="15045-161">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="15045-162">Používá nejvyšší instalovaný pruh funkcí a úroveň oprav odpovídající požadovanému hlavnímu a dílčímu pásmu s pásem funkcí, který je větší nebo roven zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="15045-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="15045-163">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="15045-164">Používá nejvyšší instalovaný podřízený, panel funkcí a úroveň oprav, které odpovídají požadované hlavní hodnotě, která je větší nebo rovna zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="15045-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="15045-165">Pokud se nenalezne, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15045-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="15045-166">Používá nejvyšší nainstalované .NET Core SDK s větší nebo rovnou zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="15045-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="15045-167">Pokud se nenalezne, selže.</span><span class="sxs-lookup"><span data-stu-id="15045-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="15045-168">Nevede k posunutí.</span><span class="sxs-lookup"><span data-stu-id="15045-168">Doesn't roll forward.</span></span> <span data-ttu-id="15045-169">Požaduje se přesná shoda.</span><span class="sxs-lookup"><span data-stu-id="15045-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="15045-170">Příklady</span><span class="sxs-lookup"><span data-stu-id="15045-170">Examples</span></span>

<span data-ttu-id="15045-171">Následující příklad ukazuje, jak používat předprodejní verze:</span><span class="sxs-lookup"><span data-stu-id="15045-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="15045-172">Následující příklad ukazuje, jak použít nejvyšší nainstalovanou verzi, která je větší nebo rovna zadané verzi:</span><span class="sxs-lookup"><span data-stu-id="15045-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="15045-173">Následující příklad ukazuje, jak použít přesně určenou verzi:</span><span class="sxs-lookup"><span data-stu-id="15045-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="15045-174">Následující příklad ukazuje, jak použít nejvyšší verzi opravy nainstalovanou specifickou verzi (ve formuláři, 3.1.1 xx):</span><span class="sxs-lookup"><span data-stu-id="15045-174">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="15045-175">Global. JSON a .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="15045-175">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="15045-176">Je užitečné zjistit, které verze sady SDK jsou nainstalovány na vašem počítači, aby je bylo možné nastavit v *globálním souboru. JSON* .</span><span class="sxs-lookup"><span data-stu-id="15045-176">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="15045-177">Další informace o tom, jak to provést, najdete v tématu [Jak ověřit, že je rozhraní .NET Core již nainstalováno](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="15045-177">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="15045-178">Pokud chcete na svém počítači nainstalovat další .NET Core SDK verze, navštivte stránku [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="15045-178">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="15045-179">Nový soubor *Global. JSON* můžete v aktuálním adresáři vytvořit spuštěním příkazu [dotnet New](dotnet-new.md) , podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15045-179">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="15045-180">Pravidla pro porovnání</span><span class="sxs-lookup"><span data-stu-id="15045-180">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="15045-181">Pravidla pro porovnání se řídí vstupním bodem `dotnet.exe`, který je společný pro všechny nainstalované moduly runtime .NET Core nainstalované v.</span><span class="sxs-lookup"><span data-stu-id="15045-181">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="15045-182">Pravidla pro porovnání pro nejnovější nainstalovanou verzi modulu runtime .NET Core se používají, když máte více nainstalovaných modulů runtime vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="15045-182">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3xtabnetcore3x"></a>[<span data-ttu-id="15045-183">.NET Core 3. x</span><span class="sxs-lookup"><span data-stu-id="15045-183">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="15045-184">Počínaje rozhraním .NET Core 3,0 se při určování používané verze sady SDK použijí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="15045-184">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="15045-185">Pokud není nalezen žádný soubor *Global. JSON* , nebo soubor *Global. JSON* neurčuje verzi sady SDK ani hodnotu `allowPrerelease`, použije se nejvyšší nainstalovaná verze sady sdk (ekvivalent nastavení `rollForward` `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="15045-185">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="15045-186">Informace o `dotnet` tom, zda jsou vyvolány verze předprodejní verze sady SDK, závisí na tom, jak je</span><span class="sxs-lookup"><span data-stu-id="15045-186">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="15045-187">Pokud nejste **v aplikaci** Visual Studio, předprodejní verze se považují za.</span><span class="sxs-lookup"><span data-stu-id="15045-187">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="15045-188">Pokud jste v aplikaci Visual Studio, použije se požadovaný stav předprodejní verze.</span><span class="sxs-lookup"><span data-stu-id="15045-188">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="15045-189">To znamená, že pokud používáte verzi Preview sady Visual Studio nebo jste nastavili náhledy **použití možnosti .NET Core SDK** (v části **nástroje** > **Možnosti** \*\* >  > \*\* **funkce verze Preview**), předprodejní verze se považují za. v opačném případě jsou zváženy pouze verze Release.</span><span class="sxs-lookup"><span data-stu-id="15045-189">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="15045-190">Pokud je nalezen soubor *Global. JSON* , který neurčuje verzi sady SDK, ale určuje `allowPrerelease` hodnotu, použije se nejvyšší nainstalovaná verze sady SDK (ekvivalent nastavení `rollForward` `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="15045-190">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="15045-191">Bez ohledu na to, zda může být vydání nejnovější verze sady SDK nebo předběžná verze, závisí na hodnotě `allowPrerelease`.</span><span class="sxs-lookup"><span data-stu-id="15045-191">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="15045-192">`true` označuje, že předprodejní verze jsou zváženy. `false` označuje, že se považují jenom verze Release.</span><span class="sxs-lookup"><span data-stu-id="15045-192">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="15045-193">Pokud je nalezen soubor *Global. JSON* a určuje verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="15045-193">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="15045-194">Pokud není nastavená žádná `rollFoward` hodnota, použije se jako výchozí zásada pro `rollForward` `latestPatch`.</span><span class="sxs-lookup"><span data-stu-id="15045-194">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="15045-195">V opačném případě Ověřte všechny hodnoty a jejich chování v části [dopředné obnovení](#rollforward) .</span><span class="sxs-lookup"><span data-stu-id="15045-195">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="15045-196">Bez ohledu na to, jestli jsou předprodejní verze zvážené a jaké je výchozí chování, když `allowPrerelease` není nastavené, je popsané v části [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="15045-196">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="15045-197">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="15045-197">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="15045-198">V sadě .NET Core 2. x SDK se při určování používané verze sady SDK použijí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="15045-198">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="15045-199">Pokud nebyl nalezen soubor *Global. JSON* nebo soubor *Global. JSON* neurčuje verzi sady SDK, bude použita nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-199">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="15045-200">Nejnovější verze sady SDK může být verze nebo předběžná verze – nejvyšší číslo verze služby WINS.</span><span class="sxs-lookup"><span data-stu-id="15045-200">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="15045-201">Pokud *Global. JSON* určí verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="15045-201">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="15045-202">Pokud je v počítači nalezena zadaná verze sady SDK, je použita tato přesná verze.</span><span class="sxs-lookup"><span data-stu-id="15045-202">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="15045-203">Pokud se zadaná verze sady SDK v tomto počítači nenajde, použije se nejnovější nainstalovaná **verze opravy** SDK této verze.</span><span class="sxs-lookup"><span data-stu-id="15045-203">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="15045-204">Nejnovější nainstalovaná **verze opravy** sady SDK může být buď verze, nebo předprodejní verze – nejvyšší číslo verze služby WINS.</span><span class="sxs-lookup"><span data-stu-id="15045-204">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="15045-205">V .NET Core 2,1 a novějších **verzích opravy** nižší, než je zadaná **verze opravy** , se v výběru sady SDK ignorují.</span><span class="sxs-lookup"><span data-stu-id="15045-205">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="15045-206">Pokud není nalezena zadaná verze sady SDK a příslušná **verze opravy** sady SDK, je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="15045-206">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="15045-207">Verze sady SDK se skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="15045-207">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="15045-208">**Verze .NET Core SDK funkce** je vyjádřena první číslicí (`x`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="15045-208">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="15045-209">Obecně platí, že .NET Core SDK má rychlejší cyklus vydávání verzí než .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15045-209">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="15045-210">**Verze opravy** je definována posledními dvěma číslicemi (`yz`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="15045-210">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="15045-211">Například pokud zadáte `2.1.300` jako verzi sady SDK, výběr sady SDK vyhledá až `2.1.399`, ale `2.1.400` není považována za verzi opravy `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="15045-211">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="15045-212">.NET Core SDK verze `2.1.100` prostřednictvím `2.1.201` byly vydány během přechodu mezi schématy čísel verzí a nesprávně nezpracovávají `xyz` notace.</span><span class="sxs-lookup"><span data-stu-id="15045-212">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="15045-213">Důrazně doporučujeme, pokud zadáte tyto verze v souboru *Global. JSON* , abyste zajistili, že zadané verze jsou na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="15045-213">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="15045-214">Řešení potíží s upozorněními sestavení</span><span class="sxs-lookup"><span data-stu-id="15045-214">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="15045-215">Pracujete s verzí Preview .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-215">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="15045-216">Verzi sady SDK můžete definovat prostřednictvím globálního souboru. JSON v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="15045-216">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="15045-217">Další na <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="15045-217">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="15045-218">Toto upozornění znamená, že projekt byl zkompilován pomocí předprodejní verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="15045-218">This warning indicates that your project was compiled using a prerelease version of the .NET Core SDK.</span></span> <span data-ttu-id="15045-219">Verze .NET Core SDK mají historii a závazek vysoké kvality.</span><span class="sxs-lookup"><span data-stu-id="15045-219">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="15045-220">Pokud ale nechcete použít předběžnou verzi, Projděte si různé strategie, které můžete použít se sadou .NET Core 3,0 SDK nebo novější verzí v části [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="15045-220">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="15045-221">Pro počítače, které nikdy nemají nainstalovanou sadu .NET Core 3,0 nebo novější modul runtime nebo sadu SDK, je třeba vytvořit soubor *Global. JSON* a zadat přesnou verzi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="15045-221">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

> [!WARNING]
> <span data-ttu-id="15045-222">Spouštěcí projekt {startupProject} cílí na rozhraní Framework. NETCoreApp verze {targetFrameworkVersion}.</span><span class="sxs-lookup"><span data-stu-id="15045-222">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="15045-223">Tato verze nástrojů příkazového řádku Entity Framework Core .NET podporuje pouze verzi 2,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="15045-223">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="15045-224">Informace o použití starších verzí nástrojů najdete v tématu <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="15045-224">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="15045-225">Počínaje sadou .NET Core 2,1 SDK (verze 2.1.300) se v sadě SDK nachází příkaz `dotnet ef`.</span><span class="sxs-lookup"><span data-stu-id="15045-225">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="15045-226">Toto upozornění znamená, že projekt cílí na EF Core 1,0 nebo 1,1, což není kompatibilní s .NET Core 2,1 SDK a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="15045-226">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="15045-227">Chcete-li zkompilovat projekt, nainstalujte sadu .NET Core 2,0 SDK (verze 2.1.201) a dřívější na váš počítač a definujte požadovanou verzi sady SDK pomocí souboru *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="15045-227">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="15045-228">Další informace o příkazu `dotnet ef` najdete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="15045-228">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="15045-229">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15045-229">See also</span></span>

- [<span data-ttu-id="15045-230">Jak se řeší sady SDK projektu</span><span class="sxs-lookup"><span data-stu-id="15045-230">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
