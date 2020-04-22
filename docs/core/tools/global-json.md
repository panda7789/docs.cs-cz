---
title: global.json – přehled
description: Přečtěte si, jak pomocí souboru global.json nastavit verzi sady .NET Core SDK při spouštění příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021347"
---
# <a name="globaljson-overview"></a><span data-ttu-id="ccc6f-103">global.json – přehled</span><span class="sxs-lookup"><span data-stu-id="ccc6f-103">global.json overview</span></span>

<span data-ttu-id="ccc6f-104">**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="ccc6f-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="ccc6f-105">Soubor *global.json* umožňuje definovat, která verze sady .NET Core SDK se používá při spuštění příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="ccc6f-106">Výběr sady .NET Core SDK je nezávislý na určení běhu cílů projektu.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="ccc6f-107">Verze sady .NET Core SDK označuje, které verze rozhraní PŘÍKAZU .NET Core CLI se používají.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="ccc6f-108">Obecně chcete použít nejnovější verzi nástrojů sady SDK, takže není potřeba žádný soubor *global.json.*</span><span class="sxs-lookup"><span data-stu-id="ccc6f-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="ccc6f-109">V některých pokročilých scénářích můžete chtít řídit verzi nástrojů sady SDK a tento článek vysvětluje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="ccc6f-110">Další informace o určení runtime místo toho naleznete v tématu [cílové architektury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ccc6f-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="ccc6f-111">Sada .NET Core SDK hledá soubor *global.json* v aktuálním pracovním adresáři (který nemusí být nutně stejný jako adresář projektu) nebo v jednom z nadřazených adresářů.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="ccc6f-112">schéma global.json</span><span class="sxs-lookup"><span data-stu-id="ccc6f-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="ccc6f-113">SDK</span><span class="sxs-lookup"><span data-stu-id="ccc6f-113">sdk</span></span>

<span data-ttu-id="ccc6f-114">Typ:`object`</span><span class="sxs-lookup"><span data-stu-id="ccc6f-114">Type: `object`</span></span>

<span data-ttu-id="ccc6f-115">Určuje informace o vybertece sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="ccc6f-116">version</span><span class="sxs-lookup"><span data-stu-id="ccc6f-116">version</span></span>

- <span data-ttu-id="ccc6f-117">Typ:`string`</span><span class="sxs-lookup"><span data-stu-id="ccc6f-117">Type: `string`</span></span>

- <span data-ttu-id="ccc6f-118">K dispozici od: .NET Core 1.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="ccc6f-119">Verze sady .NET Core SDK, která má být používána.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="ccc6f-120">Toto pole:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-120">This field:</span></span>

- <span data-ttu-id="ccc6f-121">Nemá podporu zástupných symbolů, to znamená, že musí být zadáno číslo plné verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="ccc6f-122">Nepodporuje rozsahy verzí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="ccc6f-123">allowPředběžné vydání</span><span class="sxs-lookup"><span data-stu-id="ccc6f-123">allowPrerelease</span></span>

- <span data-ttu-id="ccc6f-124">Typ:`boolean`</span><span class="sxs-lookup"><span data-stu-id="ccc6f-124">Type: `boolean`</span></span>

- <span data-ttu-id="ccc6f-125">K dispozici od: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="ccc6f-126">Označuje, zda by měl překladač sady SDK zvážit předběžné verze při výběru verze sady SDK, která má být používána.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="ccc6f-127">Pokud tuto hodnotu nenastavíte explicitně, výchozí hodnota závisí na tom, jestli používáte z Visual Studia:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="ccc6f-128">Pokud **nejste** ve Visual Studiu, výchozí `true`hodnota je .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="ccc6f-129">Pokud jste v sadě Visual Studio, používá požadovaný stav předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="ccc6f-130">To znamená, že pokud používáte verzi Preview sady Visual Studio nebo nastavíte možnost Použít náhledy sady **.NET Core SDK** (v části Funkce**náhledu** >  **prostředí tools** > **Options** > **Environment ),** je `true`výchozí hodnota ; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="ccc6f-131">rollForward</span><span class="sxs-lookup"><span data-stu-id="ccc6f-131">rollForward</span></span>

- <span data-ttu-id="ccc6f-132">Typ:`string`</span><span class="sxs-lookup"><span data-stu-id="ccc6f-132">Type: `string`</span></span>

- <span data-ttu-id="ccc6f-133">K dispozici od: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="ccc6f-134">Zásady pro předávání vpřed, které se mají použít při výběru verze sady SDK, buď jako záložní, pokud chybí konkrétní verze sady SDK, nebo jako direktivu pro použití vyšší verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="ccc6f-135">[Verze](#version) musí být zadána s hodnotou, `rollForward` pokud `latestMajor`ji nenastavujete na .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="ccc6f-136">Chcete-li porozumět dostupným zásadám a jejich chování, zvažte následující `x.y.znn`definice pro verzi sady SDK ve formátu :</span><span class="sxs-lookup"><span data-stu-id="ccc6f-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="ccc6f-137">`x`je hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-137">`x` is the major version.</span></span>
- <span data-ttu-id="ccc6f-138">`y`je dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-138">`y` is the minor version.</span></span>
- <span data-ttu-id="ccc6f-139">`z`je pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-139">`z` is the feature band.</span></span>
- <span data-ttu-id="ccc6f-140">`nn`je verze opravy.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-140">`nn` is the patch version.</span></span>

<span data-ttu-id="ccc6f-141">V následující tabulce jsou uvedeny možné hodnoty `rollForward` klíče:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="ccc6f-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ccc6f-142">Value</span></span>         | <span data-ttu-id="ccc6f-143">Chování</span><span class="sxs-lookup"><span data-stu-id="ccc6f-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="ccc6f-144">Používá zadanou verzi.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-144">Uses the specified version.</span></span> <br> <span data-ttu-id="ccc6f-145">Pokud není nalezen, převalí dopředu na nejnovější úroveň opravy.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="ccc6f-146">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="ccc6f-147">Tato hodnota je starší chování z předchozích verzí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="ccc6f-148">Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="ccc6f-149">Pokud není nalezen, převrátí se na další vyšší pásmo funkcí v rámci stejného hlavního/vedlejšího a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-150">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="ccc6f-151">Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="ccc6f-152">Pokud není nalezen, převrátí se do dalšího vyššího pásma funkcí v rámci stejné hlavní/dílčí verze a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-153">Pokud není nalezen, převrátí se na další vyšší minor a pásmo funkcí v rámci stejného hlavního a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-154">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="ccc6f-155">Používá nejnovější úroveň opravy pro zadané hlavní, menší a funkční pásmo.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="ccc6f-156">Pokud není nalezen, převrátí se do dalšího vyššího pásma funkcí v rámci stejné hlavní/dílčí verze a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-157">Pokud není nalezen, převrátí se na další vyšší minor a pásmo funkcí v rámci stejného hlavního a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-158">Pokud není nalezen, převrátí se na další vyšší hlavní, menší a funkční pásmo a použije nejnovější úroveň opravy pro toto pásmo funkcí.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="ccc6f-159">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="ccc6f-160">Používá nejnovější nainstalovanou úroveň opravy, která odpovídá požadovanému hlavnímu, menšímu a funkčnímu pásmu s úrovní opravy a která je větší nebo rovna než zadaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="ccc6f-161">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="ccc6f-162">Používá nejvyšší nainstalované pásmo funkcí a úroveň opravy, která odpovídá požadované mutovi a menší mu, s pásmem prvků, které je větší nebo rovno zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="ccc6f-163">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="ccc6f-164">Používá nejvyšší nainstalované dílčí, pásmo funkcí a úroveň opravy, která odpovídá požadované mutovi, s podřadnou, která je větší nebo rovna zadané hodnotě.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="ccc6f-165">Pokud nebyl nalezen, selže.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="ccc6f-166">Používá nejvyšší nainstalovanou sadu .NET Core SDK s hlavní, která je větší nebo rovna než zadaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="ccc6f-167">Pokud není nalezen, selhání.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="ccc6f-168">Nekupředu.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-168">Doesn't roll forward.</span></span> <span data-ttu-id="ccc6f-169">Přesná shoda nutná.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="ccc6f-170">Příklady</span><span class="sxs-lookup"><span data-stu-id="ccc6f-170">Examples</span></span>

<span data-ttu-id="ccc6f-171">Následující příklad ukazuje, jak nepoužívat předběžné verze:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="ccc6f-172">Následující příklad ukazuje, jak používat nejvyšší nainstalovanou verzi, která je větší nebo rovna než zadaná verze:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="ccc6f-173">Následující příklad ukazuje, jak používat přesně zadanou verzi:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="ccc6f-174">Následující příklad ukazuje, jak používat nejnovější pásmo funkcí a verzi opravy nainstalovanou v konkrétní hlavní a dílčí verzi:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-174">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="ccc6f-175">Následující příklad ukazuje, jak používat nejvyšší verzi opravy nainstalovanou pro konkrétní verzi (ve formuláři 3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="ccc6f-175">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="ccc6f-176">global.json a rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="ccc6f-176">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="ccc6f-177">Je užitečné vědět, které verze sady SDK jsou nainstalovány v počítači a nastavit je v souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="ccc6f-177">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="ccc6f-178">Další informace o tom, jak to provést, naleznete v [tématu Jak zkontrolovat, zda je jádro .NET Core již nainstalováno](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="ccc6f-178">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="ccc6f-179">Chcete-li do počítače nainstalovat další verze sady .NET Core SDK, navštivte stránku [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-179">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="ccc6f-180">Nový soubor *global.json* můžete vytvořit v aktuálním adresáři spuštěním nového příkazu [dotnet,](dotnet-new.md) podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-180">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="ccc6f-181">Pravidla párování</span><span class="sxs-lookup"><span data-stu-id="ccc6f-181">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="ccc6f-182">Pravidla párování se řídí `dotnet.exe` vstupním bodem, který je společný pro všechny nainstalované runtimesy nainstalované rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-182">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="ccc6f-183">Pravidla párování pro nejnovější nainstalovanou verzi rozhraní .NET Core Runtime se používají, pokud máte vedle sebe nainstalováno více runtimeů.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-183">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="ccc6f-184">.NET Jádro 3.x</span><span class="sxs-lookup"><span data-stu-id="ccc6f-184">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="ccc6f-185">Počínaje rozhraním .NET Core 3.0 platí při určování, kterou verzi sady SDK použít, následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-185">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="ccc6f-186">Pokud není nalezen žádný soubor *global.json* nebo *global.json* neurčuje verzi `allowPrerelease` sady SDK ani hodnotu, použije `rollForward` se `latestMajor`nejvyšší nainstalovaná verze sady SDK (ekvivalentní nastavení).</span><span class="sxs-lookup"><span data-stu-id="ccc6f-186">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="ccc6f-187">Zda předběžné verze sady SDK jsou `dotnet` považovány za závisí na jak je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-187">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="ccc6f-188">Pokud **nejste** v sadě Visual Studio, jsou považovány za předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-188">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="ccc6f-189">Pokud jste v sadě Visual Studio, používá požadovaný stav předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-189">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="ccc6f-190">To znamená, že pokud používáte verzi Preview sady Visual Studio nebo nastavíte **použít náhledy možnosti .NET Core SDK** (v části **Tools** > **Options** > **Environment** > **Preview Features),** budou předběžné verze považovány za; v opačném případě jsou považovány pouze verze verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-190">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="ccc6f-191">Pokud je nalezen soubor *global.json,* který neurčuje verzi sady SDK, ale určuje hodnotu, `allowPrerelease` použije se `rollForward` `latestMajor`nejvyšší nainstalovaná verze sady SDK (ekvivalentní nastavení ).</span><span class="sxs-lookup"><span data-stu-id="ccc6f-191">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="ccc6f-192">To, zda nejnovější verze sady SDK může být `allowPrerelease`vydána nebo předběžná verze, závisí na hodnotě aplikace .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-192">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="ccc6f-193">`true`označuje, že jsou zváženy předběžné verze; `false` označuje, že jsou považovány pouze verze vydání.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-193">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="ccc6f-194">Pokud je nalezen soubor *global.json* a určuje verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-194">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="ccc6f-195">Pokud `rollFoward` není nastavena žádná `latestPatch` hodnota, `rollForward` použije se jako výchozí zásada.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-195">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="ccc6f-196">V opačném případě zkontrolujte každou hodnotu a jejich chování v části [rollForward.](#rollforward)</span><span class="sxs-lookup"><span data-stu-id="ccc6f-196">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="ccc6f-197">Zda předběžné verze jsou považovány za a co `allowPrerelease` je výchozí chování, když není nastavena je popsána v [allowPrerelease](#allowprerelease) části.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-197">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="ccc6f-198">.NET Jádro 2.x</span><span class="sxs-lookup"><span data-stu-id="ccc6f-198">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ccc6f-199">V sdk .NET Core 2.x Platí následující pravidla při určování, kterou verzi sady SDK použít:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-199">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="ccc6f-200">Pokud není nalezen žádný soubor *global.json* nebo *global.json* neurčuje verzi sady SDK, použije se nejnovější nainstalovaná verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-200">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="ccc6f-201">Nejnovější verze sady SDK může být buď vydána, nebo předběžná verze - nejvyšší číslo verze vyhrává.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-201">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="ccc6f-202">Pokud *global.json* určit verzi sady SDK:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-202">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="ccc6f-203">Pokud je v počítači nalezena zadaná verze sady SDK, použije se tato přesná verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-203">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="ccc6f-204">Pokud zadanou verzi sady SDK nelze v počítači najít, bude použita nejnovější nainstalovaná **verze opravy** sady SDK této verze.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-204">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="ccc6f-205">Nejnovější nainstalovaná **verze opravy** Sady SDK může být buď vydána, nebo předběžná verze - nejvyšší číslo verze vyhrává.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-205">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="ccc6f-206">V rozhraní .NET Core 2.1 a vyšší jsou **verze opravy** nižší než zadaná **verze opravy** ve výběru sady SDK ignorovány.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-206">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="ccc6f-207">Pokud zadanou verzi sady SDK a příslušnou **verzi opravy** sady SDK nelze najít, je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-207">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="ccc6f-208">Verze sady SDK se skládá z následujících částí:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-208">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="ccc6f-209">**Verze funkce** sady .NET Core SDK je reprezentována první číslicí (`x`) v poslední části čísla (`xyz`) pro sady SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-209">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="ccc6f-210">Obecně platí, že sada .NET Core SDK má rychlejší cyklus vydání než .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-210">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="ccc6f-211">**Verze opravy** je definována posledními`yz`dvěma číslicemi (`xyz`) v poslední části čísla ( ) pro sady SDK verze 2.1.100 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-211">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="ccc6f-212">Pokud například zadáte `2.1.300` jako verzi sady SDK, výběr `2.1.399` sady `2.1.400` SDK najde až `2.1.300`do, ale není považován za verzi opravy pro .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-212">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="ccc6f-213">Verze sady .NET Core `2.1.100` `2.1.201` SDK byly vydány během přechodu mezi schématy čísel verzí a zápis nezpracovávají `xyz` správně.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-213">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="ccc6f-214">Důrazně doporučujeme, pokud zadáte tyto verze v souboru *global.json,* ujistěte se, že zadané verze jsou na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-214">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="ccc6f-215">Poradce při potížích s upozorněními na sestavení</span><span class="sxs-lookup"><span data-stu-id="ccc6f-215">Troubleshoot build warnings</span></span>

* <span data-ttu-id="ccc6f-216">Následující upozornění označuje, že váš projekt byl zkompilován pomocí předběžné verze sady .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-216">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="ccc6f-217">Pracujete s verzí preview sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-217">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="ccc6f-218">Verzi sady SDK můžete definovat prostřednictvím souboru global.json v aktuálním projektu.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-218">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="ccc6f-219">Více <https://go.microsoft.com/fwlink/?linkid=869452>na .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-219">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="ccc6f-220">Verze sady .NET Core SDK mají historii a závazek vysoké kvality.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-220">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="ccc6f-221">Pokud však nechcete používat předběžnou verzi, zkontrolujte různé strategie, které můžete použít s sadou .NET Core 3.0 SDK nebo novější verzí v části [allowPrerelease.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="ccc6f-221">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="ccc6f-222">U počítačů, které nikdy neměly nainstalovanou runtime .NET Core 3.0 nebo vyšší nebo sdk, je třeba vytvořit soubor *global.json* a zadat přesnou verzi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-222">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="ccc6f-223">Následující upozornění označuje, že váš projekt cíle EF Core 1.0 nebo 1.1, který není kompatibilní s .NET Core 2.1 SDK a novější verze:</span><span class="sxs-lookup"><span data-stu-id="ccc6f-223">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="ccc6f-224">Projekt spuštění projektu {startupProject} cílí na rozhraní ". NETCoreApp' verze '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-224">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="ccc6f-225">Tato verze nástrojů příkazového řádku entity Framework .NET .NET podporuje pouze verzi 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-225">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="ccc6f-226">Informace o používání starších verzí nástrojů <https://go.microsoft.com/fwlink/?linkid=871254>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="ccc6f-226">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="ccc6f-227">Počínaje .NET Core 2.1 SDK (verze 2.1.300), `dotnet ef` příkaz je součástí sady SDK.</span><span class="sxs-lookup"><span data-stu-id="ccc6f-227">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="ccc6f-228">Chcete-li zkompilovat projekt, nainstalujte do počítače sady .NET Core 2.0 SDK (verze 2.1.201) nebo starší a definujte požadovanou verzi sady SDK pomocí souboru *global.json.*</span><span class="sxs-lookup"><span data-stu-id="ccc6f-228">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="ccc6f-229">Další informace o `dotnet ef` příkazu naleznete v tématu [EF Core .NET Nástroje příkazového řádku](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="ccc6f-229">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc6f-230">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccc6f-230">See also</span></span>

- [<span data-ttu-id="ccc6f-231">Jak jsou sady SDK projektu vyřešeny</span><span class="sxs-lookup"><span data-stu-id="ccc6f-231">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
