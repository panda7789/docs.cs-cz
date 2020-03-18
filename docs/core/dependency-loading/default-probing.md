---
title: Výchozí zjišťování - .NET Core
description: Přehled logiky zjišťování .NET Core System.Runtime.Loader.AssemblyLoadContext.Default pro hledání závislostí.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399089"
---
# <a name="default-probing"></a><span data-ttu-id="71bbf-103">Výchozí zjišťování</span><span class="sxs-lookup"><span data-stu-id="71bbf-103">Default probing</span></span>

<span data-ttu-id="71bbf-104">Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> je zodpovědná za vyhledání závislostí sestavení.</span><span class="sxs-lookup"><span data-stu-id="71bbf-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="71bbf-105">Tento článek popisuje <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logiku zjišťování instance.</span><span class="sxs-lookup"><span data-stu-id="71bbf-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="71bbf-106">Vlastnosti zjišťování nakonfigurované hostitelem</span><span class="sxs-lookup"><span data-stu-id="71bbf-106">Host configured probing properties</span></span>

<span data-ttu-id="71bbf-107">Při spuštění runtime hostitel runtime poskytuje sadu pojmenovaných vlastností <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zjišťování, které konfigurují cesty promoru.</span><span class="sxs-lookup"><span data-stu-id="71bbf-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="71bbf-108">Každá vlastnost zjišťování je volitelná.</span><span class="sxs-lookup"><span data-stu-id="71bbf-108">Each probing property is optional.</span></span> <span data-ttu-id="71bbf-109">Pokud je k dispozici, každá vlastnost je řetězcová hodnota, která obsahuje oddělený seznam absolutních cest.</span><span class="sxs-lookup"><span data-stu-id="71bbf-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="71bbf-110">Oddělovač je ';' v systému Windows a ':' na všech ostatních platformách.</span><span class="sxs-lookup"><span data-stu-id="71bbf-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="71bbf-111">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="71bbf-111">Property Name</span></span>                 |<span data-ttu-id="71bbf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="71bbf-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="71bbf-113">Seznam cest souborů sestavení platformy a aplikace.</span><span class="sxs-lookup"><span data-stu-id="71bbf-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="71bbf-114">Seznam cest adresářů pro vyhledávání satelitních sestavení prostředků.</span><span class="sxs-lookup"><span data-stu-id="71bbf-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="71bbf-115">Seznam cest adresářů pro vyhledávání nespravovaných (nativních) knihoven.</span><span class="sxs-lookup"><span data-stu-id="71bbf-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="71bbf-116">Seznam cest adresáře pro vyhledávání spravovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="71bbf-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="71bbf-117">Seznam cest adresáře pro vyhledávání nativních bitových kopií spravovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="71bbf-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="71bbf-118">Jak jsou vlastnosti naplněny?</span><span class="sxs-lookup"><span data-stu-id="71bbf-118">How are the properties populated?</span></span>

<span data-ttu-id="71bbf-119">Existují dva hlavní scénáře pro vyplnění vlastnosti v závislosti na tom, zda existuje soubor \* \<myapp>.deps.json.\*</span><span class="sxs-lookup"><span data-stu-id="71bbf-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="71bbf-120">Pokud je soubor \* \*.deps.json\* přítomen, je analyzován k naplnění vlastností zjišťování.</span><span class="sxs-lookup"><span data-stu-id="71bbf-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="71bbf-121">Pokud soubor \* \*.deps.json\* není k dispozici, předpokládá se, že adresář aplikace obsahuje všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="71bbf-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="71bbf-122">Obsah adresáře se používá k naplnění vlastností zjišťování.</span><span class="sxs-lookup"><span data-stu-id="71bbf-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="71bbf-123">Kromě toho \* \*jsou\* podobně analyzovány soubory .deps.json pro všechny odkazované architektury.</span><span class="sxs-lookup"><span data-stu-id="71bbf-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="71bbf-124">Nakonec proměnné `ADDITIONAL_DEPS` prostředí lze přidat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="71bbf-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="71bbf-125">Jak zobrazím vlastnosti zjišťování ze spravovaného kódu?</span><span class="sxs-lookup"><span data-stu-id="71bbf-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="71bbf-126">Každá vlastnost je k <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> dispozici voláním funkce s názvem vlastnosti z výše uvedené tabulky.</span><span class="sxs-lookup"><span data-stu-id="71bbf-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="71bbf-127">Jak lze ladit konstrukci vlastností sondování?</span><span class="sxs-lookup"><span data-stu-id="71bbf-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="71bbf-128">Hostitel runtime .NET Core bude výstupem užitečných trasovacích zpráv, pokud jsou povoleny určité proměnné prostředí:</span><span class="sxs-lookup"><span data-stu-id="71bbf-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="71bbf-129">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="71bbf-129">Environment Variable</span></span>        |<span data-ttu-id="71bbf-130">Popis</span><span class="sxs-lookup"><span data-stu-id="71bbf-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="71bbf-131">Povolí trasování.</span><span class="sxs-lookup"><span data-stu-id="71bbf-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="71bbf-132">Trasování na cestu k souboru namísto výchozí `stderr`.</span><span class="sxs-lookup"><span data-stu-id="71bbf-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="71bbf-133">Nastaví podrobnost z 1 (nejnižší) na 4 (nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="71bbf-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="71bbf-134">Výchozí zjišťování spravovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="71bbf-134">Managed assembly default probing</span></span>

<span data-ttu-id="71bbf-135">Při zjišťování najít spravované sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> vypadá v pořadí na adrese:</span><span class="sxs-lookup"><span data-stu-id="71bbf-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="71bbf-136">Soubory odpovídající <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` in (po odebrání přípony souborů).</span><span class="sxs-lookup"><span data-stu-id="71bbf-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="71bbf-137">Nativní soubory `APP_NI_PATHS` sestavení obrazu s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="71bbf-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="71bbf-138">Soubory sestavení `APP_PATHS` v s běžnými příponami souborů.</span><span class="sxs-lookup"><span data-stu-id="71bbf-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="71bbf-139">Satelitní (zdroj) zjišťování sestavení</span><span class="sxs-lookup"><span data-stu-id="71bbf-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="71bbf-140">Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, vytvořte sadu cest souborů.</span><span class="sxs-lookup"><span data-stu-id="71bbf-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="71bbf-141">Pro každou `PLATFORM_RESOURCE_ROOTS` cestu `APP_PATHS`v a <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> potom připojit řetězec, oddělovač adresářů, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> řetězec a rozšíření '.dll'.</span><span class="sxs-lookup"><span data-stu-id="71bbf-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="71bbf-142">Pokud existuje nějaký odpovídající soubor, pokuste se jej načíst a vrátit.</span><span class="sxs-lookup"><span data-stu-id="71bbf-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="71bbf-143">Nespravované (nativní) sondování knihovny</span><span class="sxs-lookup"><span data-stu-id="71bbf-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="71bbf-144">Při zjišťování vyhledat nespravované knihovny, `NATIVE_DLL_SEARCH_DIRECTORIES` jsou prohledány hledá odpovídající knihovny.</span><span class="sxs-lookup"><span data-stu-id="71bbf-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
