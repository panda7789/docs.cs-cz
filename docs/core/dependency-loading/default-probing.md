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
# <a name="default-probing"></a>Výchozí zjišťování

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zodpovídá za vyhledání závislostí sestavení. Tento článek popisuje logiku probingu instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

## <a name="host-configured-probing-properties"></a>Vlastnosti služby probingu konfigurované pro hostitele

Po spuštění modulu runtime poskytuje hostitel modulu runtime sadu pojmenovaných vlastností zjišťování, které konfigurují cesty testu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

Každá vlastnost probingu je volitelná. Pokud je tato vlastnost k dispozici, je hodnota řetězce, která obsahuje oddělený seznam absolutních cest. Oddělovač je '; ' ve Windows a ': ' na všech ostatních platformách.

|Název vlastnosti                 |Popis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Seznam cest k souborům sestavení platformy a aplikace |
|`PLATFORM_RESOURCE_ROOTS`       | Seznam cest k adresářům pro hledání satelitních sestavení prostředků |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Seznam cest adresáře, ve kterých se mají hledat nespravované (nativní) knihovny.        |
|`APP_PATHS`                     | Seznam cest adresáře, ve kterých se mají vyhledávat spravovaná sestavení |
|`APP_NI_PATHS`                  | Seznam cest adresáře, ve kterých se mají vyhledávat nativní bitové kopie spravovaných sestavení |

### <a name="how-are-the-properties-populated"></a>Jak se naplní vlastnosti?

Existují dva hlavní scénáře pro naplnění vlastností v závislosti na tom, zda existuje soubor *\<myapp >. JSON* .

- Když je přítomen soubor *@no__t -1. DEPS. JSON* , analyzuje se, aby se naplnily vlastnosti probingu.
- Pokud soubor *@no__t -1. DEPS. JSON* neexistuje, předpokládá se, že adresář aplikace obsahuje všechny závislosti. Obsah adresáře slouží k naplnění vlastností probingu.

Navíc se analyzují soubory *@no__t -1. DEPS. JSON* pro všechny odkazované architektury.

Nakonec můžete k přidání dalších závislostí použít proměnnou prostředí `ADDITIONAL_DEPS`.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Návody zobrazit vlastnosti zjišťování ze spravovaného kódu?

Jednotlivé vlastnosti jsou k dispozici voláním funkce <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> s názvem vlastnosti z tabulky výše.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Návody ladit konstrukci vlastností probingu?

Hostitel modulu runtime .NET Core bude výstupem užitečných zpráv trasování, když jsou povolené určité proměnné prostředí:

|Proměnná prostředí        |Popis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Povolí trasování.|
|`COREHOST_TRACEFILE=<path>` |Sleduje na cestu k souboru místo výchozí `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Nastaví podrobnost z hodnoty 1 (nejnižší) na 4 (nejvyšší).|

## <a name="managed-assembly-default-probing"></a>Výchozí zjišťování spravovaného sestavení

Když zjistíte, že zjišťování vyhledá spravované sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> vypadá v pořadí:

- Soubory, které odpovídají <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> v `TRUSTED_PLATFORM_ASSEMBLIES` (po odebrání přípon souborů).
- Soubory sestavení nativní bitové kopie v `APP_NI_PATHS` s běžnými příponami souborů.
- Soubory sestavení v `APP_PATHS` s běžnými příponami souborů.

## <a name="satellite-resource-assembly-probing"></a>Satelitní zjišťování sestavení (prostředků)

Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, Sestavte sadu cest k souborům.

Pro každou cestu v `PLATFORM_RESOURCE_ROOTS` a pak `APP_PATHS` přidejte řetězec <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>, oddělovač adresáře, řetězec @no__t 3 a příponu. dll.

Pokud existuje libovolný vyhovující soubor, pokuste se ho načíst a vrátit.

## <a name="unmanaged-native-library-probing"></a>Nespravované (nativní) knihovny Bingu

Když zjistíte, že zjišťování nespravované knihovny najde, vyhledá se `NATIVE_DLL_SEARCH_DIRECTORIES`, kde se vyhledávají vyhovující knihovny.
