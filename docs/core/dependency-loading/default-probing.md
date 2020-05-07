---
title: Výchozí zjišťování – .NET Core
description: Přehled systému .NET Core System. Runtime. Loader. AssemblyLoadContext. výchozí logika pro vyhledávání závislostí.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859510"
---
# <a name="default-probing"></a><span data-ttu-id="0af57-103">Výchozí zjišťování</span><span class="sxs-lookup"><span data-stu-id="0af57-103">Default probing</span></span>

<span data-ttu-id="0af57-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Instance zodpovídá za vyhledání závislostí sestavení.</span><span class="sxs-lookup"><span data-stu-id="0af57-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="0af57-105">Tento článek popisuje logiku <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probingu instance.</span><span class="sxs-lookup"><span data-stu-id="0af57-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="0af57-106">Vlastnosti služby probingu konfigurované pro hostitele</span><span class="sxs-lookup"><span data-stu-id="0af57-106">Host configured probing properties</span></span>

<span data-ttu-id="0af57-107">Po spuštění modulu runtime poskytuje hostitel modulu runtime sadu pojmenovaných vlastností Bingu, které konfigurují <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cesty testu paměti.</span><span class="sxs-lookup"><span data-stu-id="0af57-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="0af57-108">Každá vlastnost probingu je volitelná.</span><span class="sxs-lookup"><span data-stu-id="0af57-108">Each probing property is optional.</span></span> <span data-ttu-id="0af57-109">Pokud je tato vlastnost k dispozici, je hodnota řetězce, která obsahuje oddělený seznam absolutních cest.</span><span class="sxs-lookup"><span data-stu-id="0af57-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="0af57-110">Oddělovač je '; ' ve Windows a ': ' na všech ostatních platformách.</span><span class="sxs-lookup"><span data-stu-id="0af57-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="0af57-111">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0af57-111">Property Name</span></span>                 |<span data-ttu-id="0af57-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0af57-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="0af57-113">Seznam cest k souborům sestavení platformy a aplikace</span><span class="sxs-lookup"><span data-stu-id="0af57-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="0af57-114">Seznam cest k adresářům pro hledání satelitních sestavení prostředků</span><span class="sxs-lookup"><span data-stu-id="0af57-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="0af57-115">Seznam cest adresáře, ve kterých se mají hledat nespravované (nativní) knihovny.</span><span class="sxs-lookup"><span data-stu-id="0af57-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="0af57-116">Seznam cest adresáře, ve kterých se mají vyhledávat spravovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="0af57-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="0af57-117">Seznam cest adresáře, ve kterých se mají vyhledávat nativní bitové kopie spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="0af57-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="0af57-118">Jak se naplní vlastnosti?</span><span class="sxs-lookup"><span data-stu-id="0af57-118">How are the properties populated?</span></span>

<span data-ttu-id="0af57-119">Existují dva hlavní scénáře pro naplnění vlastností v závislosti na tom, zda existuje soubor \* \<MyApp>. DEPS. JSON\* .</span><span class="sxs-lookup"><span data-stu-id="0af57-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="0af57-120">Pokud se nachází soubor \* \*. DEPS. JSON\* , analyzuje se, aby se naplnily vlastnosti probingu.</span><span class="sxs-lookup"><span data-stu-id="0af57-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="0af57-121">Pokud soubor \* \*. DEPS. JSON\* neexistuje, předpokládá se, že adresář aplikace obsahuje všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="0af57-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="0af57-122">Obsah adresáře slouží k naplnění vlastností probingu.</span><span class="sxs-lookup"><span data-stu-id="0af57-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="0af57-123">Navíc se analyzují soubory \* \*. DEPS. JSON\* pro všechny odkazované architektury.</span><span class="sxs-lookup"><span data-stu-id="0af57-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="0af57-124">Nakonec můžete k přidání `ADDITIONAL_DEPS` dalších závislostí použít proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="0af57-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

<span data-ttu-id="0af57-125">Ve `APP_PATHS` výchozím `APP_NI_PATHS` nastavení nejsou naplněny vlastnosti a a pro většinu aplikací jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="0af57-125">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="0af57-126">Návody zobrazit vlastnosti zjišťování ze spravovaného kódu?</span><span class="sxs-lookup"><span data-stu-id="0af57-126">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="0af57-127">Jednotlivé vlastnosti jsou k dispozici voláním <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkce s názvem vlastnosti z tabulky výše.</span><span class="sxs-lookup"><span data-stu-id="0af57-127">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="0af57-128">Návody ladit konstrukci vlastností probingu?</span><span class="sxs-lookup"><span data-stu-id="0af57-128">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="0af57-129">Hostitel modulu runtime .NET Core bude výstupem užitečných zpráv trasování, když jsou povolené určité proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="0af57-129">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="0af57-130">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="0af57-130">Environment Variable</span></span>        |<span data-ttu-id="0af57-131">Popis</span><span class="sxs-lookup"><span data-stu-id="0af57-131">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="0af57-132">Povolí trasování.</span><span class="sxs-lookup"><span data-stu-id="0af57-132">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="0af57-133">Vykreslí místo výchozího `stderr`umístění cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="0af57-133">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="0af57-134">Nastaví podrobnost z hodnoty 1 (nejnižší) na 4 (nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="0af57-134">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="0af57-135">Výchozí zjišťování spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="0af57-135">Managed assembly default probing</span></span>

<span data-ttu-id="0af57-136">Když zjistíte, že <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zjišťování má spravované sestavení, vypadá v pořadí:</span><span class="sxs-lookup"><span data-stu-id="0af57-136">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="0af57-137">Soubory, které <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> odpovídají `TRUSTED_PLATFORM_ASSEMBLIES` (po odebrání přípon souborů).</span><span class="sxs-lookup"><span data-stu-id="0af57-137">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="0af57-138">Soubory sestavení nativní bitové kopie `APP_NI_PATHS` v nástroji s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="0af57-138">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="0af57-139">Soubory sestavení v `APP_PATHS` nástroji s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="0af57-139">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="0af57-140">Satelitní zjišťování sestavení (prostředků)</span><span class="sxs-lookup"><span data-stu-id="0af57-140">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="0af57-141">Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, Sestavte sadu cest k souborům.</span><span class="sxs-lookup"><span data-stu-id="0af57-141">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="0af57-142">Pro každou cestu v `PLATFORM_RESOURCE_ROOTS` a potom `APP_PATHS`přidejte <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> řetězec, oddělovač adresáře, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> řetězec a příponu. dll.</span><span class="sxs-lookup"><span data-stu-id="0af57-142">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="0af57-143">Pokud existuje libovolný vyhovující soubor, pokuste se ho načíst a vrátit.</span><span class="sxs-lookup"><span data-stu-id="0af57-143">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="0af57-144">Nespravované (nativní) knihovny Bingu</span><span class="sxs-lookup"><span data-stu-id="0af57-144">Unmanaged (native) library probing</span></span>

<span data-ttu-id="0af57-145">Když zjistíte, že `NATIVE_DLL_SEARCH_DIRECTORIES` zjišťování nespravované knihovny najde, prohledávají se hledání vyhovující knihovny.</span><span class="sxs-lookup"><span data-stu-id="0af57-145">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
