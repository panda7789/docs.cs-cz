---
title: Výchozí zjišťování – .NET Core
description: Přehled systému .NET Core System. Runtime. Loader. AssemblyLoadContext. výchozí logika pro vyhledávání závislostí.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031829"
---
# <a name="default-probing"></a><span data-ttu-id="ca51b-103">Výchozí zjišťování</span><span class="sxs-lookup"><span data-stu-id="ca51b-103">Default probing</span></span>

<span data-ttu-id="ca51b-104">Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zodpovídá za vyhledání závislostí sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca51b-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="ca51b-105">Tento článek popisuje logiku probingu instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca51b-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="ca51b-106">Vlastnosti služby probingu konfigurované pro hostitele</span><span class="sxs-lookup"><span data-stu-id="ca51b-106">Host configured probing properties</span></span>

<span data-ttu-id="ca51b-107">Po spuštění modulu runtime poskytuje hostitel modulu runtime sadu pojmenovaných vlastností Bingu, které konfigurují <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cesty testu.</span><span class="sxs-lookup"><span data-stu-id="ca51b-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="ca51b-108">Každá vlastnost probingu je volitelná.</span><span class="sxs-lookup"><span data-stu-id="ca51b-108">Each probing property is optional.</span></span> <span data-ttu-id="ca51b-109">Pokud je tato vlastnost k dispozici, je hodnota řetězce, která obsahuje oddělený seznam absolutních cest.</span><span class="sxs-lookup"><span data-stu-id="ca51b-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="ca51b-110">Oddělovač je '; ' ve Windows a ': ' na všech ostatních platformách.</span><span class="sxs-lookup"><span data-stu-id="ca51b-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="ca51b-111">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ca51b-111">Property Name</span></span>                 |<span data-ttu-id="ca51b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ca51b-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="ca51b-113">Seznam cest k souborům sestavení platformy a aplikace</span><span class="sxs-lookup"><span data-stu-id="ca51b-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="ca51b-114">Seznam cest k adresářům pro hledání satelitních sestavení prostředků</span><span class="sxs-lookup"><span data-stu-id="ca51b-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="ca51b-115">Seznam cest adresáře, ve kterých se mají hledat nespravované (nativní) knihovny.</span><span class="sxs-lookup"><span data-stu-id="ca51b-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="ca51b-116">Seznam cest adresáře, ve kterých se mají vyhledávat spravovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="ca51b-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="ca51b-117">Seznam cest adresáře, ve kterých se mají vyhledávat nativní bitové kopie spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="ca51b-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="ca51b-118">Jak se naplní vlastnosti?</span><span class="sxs-lookup"><span data-stu-id="ca51b-118">How are the properties populated?</span></span>

<span data-ttu-id="ca51b-119">Existují dva hlavní scénáře pro naplnění vlastností v závislosti na tom, zda existuje soubor *\<myapp >. DEPS. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ca51b-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="ca51b-120">Když je přítomen soubor *\*. DEPS. JSON* , analyzuje se, aby se naplnily vlastnosti probingu.</span><span class="sxs-lookup"><span data-stu-id="ca51b-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="ca51b-121">Pokud soubor *\*. DEPS. JSON* neexistuje, předpokládá se, že adresář aplikace obsahuje všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="ca51b-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="ca51b-122">Obsah adresáře slouží k naplnění vlastností probingu.</span><span class="sxs-lookup"><span data-stu-id="ca51b-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="ca51b-123">Navíc se analyzují soubory *\*. DEPS. JSON* pro všechny odkazované architektury.</span><span class="sxs-lookup"><span data-stu-id="ca51b-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="ca51b-124">Nakonec lze pomocí proměnné prostředí `ADDITIONAL_DEPS` přidat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="ca51b-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="ca51b-125">Návody zobrazit vlastnosti zjišťování ze spravovaného kódu?</span><span class="sxs-lookup"><span data-stu-id="ca51b-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="ca51b-126">Jednotlivé vlastnosti jsou k dispozici voláním funkce <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> s názvem vlastnosti z tabulky výše.</span><span class="sxs-lookup"><span data-stu-id="ca51b-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="ca51b-127">Návody ladit konstrukci vlastností probingu?</span><span class="sxs-lookup"><span data-stu-id="ca51b-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="ca51b-128">Hostitel modulu runtime .NET Core bude výstupem užitečných zpráv trasování, když jsou povolené určité proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="ca51b-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="ca51b-129">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="ca51b-129">Environment Variable</span></span>        |<span data-ttu-id="ca51b-130">Popis</span><span class="sxs-lookup"><span data-stu-id="ca51b-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="ca51b-131">Povolí trasování.</span><span class="sxs-lookup"><span data-stu-id="ca51b-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="ca51b-132">Sleduje na cestu k souboru namísto výchozího `stderr`.</span><span class="sxs-lookup"><span data-stu-id="ca51b-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="ca51b-133">Nastaví podrobnost z hodnoty 1 (nejnižší) na 4 (nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="ca51b-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="ca51b-134">Výchozí zjišťování spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca51b-134">Managed assembly default probing</span></span>

<span data-ttu-id="ca51b-135">Když zjistíte, že zjišťování vyhledá spravované sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> v pořadí:</span><span class="sxs-lookup"><span data-stu-id="ca51b-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="ca51b-136">Soubory, které odpovídají <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> v `TRUSTED_PLATFORM_ASSEMBLIES` (po odebrání přípon souborů).</span><span class="sxs-lookup"><span data-stu-id="ca51b-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="ca51b-137">Soubory sestavení nativní bitové kopie v `APP_NI_PATHS` s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="ca51b-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="ca51b-138">Soubory sestavení v `APP_PATHS` s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="ca51b-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="ca51b-139">Satelitní zjišťování sestavení (prostředků)</span><span class="sxs-lookup"><span data-stu-id="ca51b-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="ca51b-140">Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, Sestavte sadu cest k souborům.</span><span class="sxs-lookup"><span data-stu-id="ca51b-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="ca51b-141">Pro každou cestu v `PLATFORM_RESOURCE_ROOTS` a potom `APP_PATHS`, přidejte <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> řetězec, oddělovač adresáře, řetězec <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> a příponu. dll.</span><span class="sxs-lookup"><span data-stu-id="ca51b-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="ca51b-142">Pokud existuje libovolný vyhovující soubor, pokuste se ho načíst a vrátit.</span><span class="sxs-lookup"><span data-stu-id="ca51b-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="ca51b-143">Nespravované (nativní) knihovny Bingu</span><span class="sxs-lookup"><span data-stu-id="ca51b-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="ca51b-144">Když zjistíte, že zjišťování nespravované knihovny vyhledá, `NATIVE_DLL_SEARCH_DIRECTORIES` se vyhledají vyhovující knihovny.</span><span class="sxs-lookup"><span data-stu-id="ca51b-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
