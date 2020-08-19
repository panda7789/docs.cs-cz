---
title: Výchozí zjišťování – .NET Core
description: Přehled systému .NET Core System. Runtime. Loader. AssemblyLoadContext. výchozí logika pro vyhledávání závislostí.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608425"
---
# <a name="default-probing"></a>Výchozí zjišťování

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>Instance zodpovídá za vyhledání závislostí sestavení. Tento článek popisuje <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logiku probingu instance.

## <a name="host-configured-probing-properties"></a>Vlastnosti služby probingu konfigurované pro hostitele

Po spuštění modulu runtime poskytuje hostitel modulu runtime sadu pojmenovaných vlastností Bingu, které konfigurují <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cesty testu paměti.

Každá vlastnost probingu je volitelná. Pokud je tato vlastnost k dispozici, je hodnota řetězce, která obsahuje oddělený seznam absolutních cest. Oddělovač je '; ' ve Windows a ': ' na všech ostatních platformách.

|Název vlastnosti                 |Popis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Seznam cest k souborům sestavení platformy a aplikace |
|`PLATFORM_RESOURCE_ROOTS`       | Seznam cest k adresářům pro hledání satelitních sestavení prostředků |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Seznam cest adresáře, ve kterých se mají hledat nespravované (nativní) knihovny.        |
|`APP_PATHS`                     | Seznam cest adresáře, ve kterých se mají vyhledávat spravovaná sestavení |
|`APP_NI_PATHS`                  | Seznam cest adresáře, ve kterých se mají vyhledávat nativní bitové kopie spravovaných sestavení |

### <a name="how-are-the-properties-populated"></a>Jak se naplní vlastnosti?

Existují dva hlavní scénáře pro vyplnění vlastností v závislosti na tom, zda * \<myapp>.deps.js* soubor existuje.

- Když se * \*.deps.jsv* souboru nachází, analyzuje se, aby se naplnily vlastnosti probingu.
- Pokud * \*.deps.jsv* souboru neexistuje, předpokládá se, že adresář aplikace obsahuje všechny závislosti. Obsah adresáře slouží k naplnění vlastností probingu.

Kromě toho * \*.deps.js* soubory pro všechny odkazované architektury se podobně analyzují.

Nakonec `ADDITIONAL_DEPS` můžete k přidání dalších závislostí použít proměnnou prostředí.  `dotnet.exe` obsahuje také `--additional-deps` volitelný parametr pro nastavení této hodnoty při spuštění aplikace.

`APP_PATHS` `APP_NI_PATHS` Ve výchozím nastavení nejsou naplněny vlastnosti a a pro většinu aplikací jsou vynechány.

K seznamu všech * \*.deps.js* souborů, které aplikace používá, se dá dostat prostřednictvím `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` .

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Návody zobrazit vlastnosti zjišťování ze spravovaného kódu?

Jednotlivé vlastnosti jsou k dispozici voláním <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkce s názvem vlastnosti z tabulky výše.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Návody ladit konstrukci vlastností probingu?

Hostitel modulu runtime .NET Core bude výstupem užitečných zpráv trasování, když jsou povolené určité proměnné prostředí:

|Proměnná prostředí        |Popis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Povolí trasování.|
|`COREHOST_TRACEFILE=<path>` |Vykreslí místo výchozího umístění cestu k souboru `stderr` .|
|`COREHOST_TRACE_VERBOSITY`  |Nastaví podrobnost z hodnoty 1 (nejnižší) na 4 (nejvyšší).|

## <a name="managed-assembly-default-probing"></a>Výchozí zjišťování spravovaného sestavení

Když zjistíte, že zjišťování má spravované sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> vypadá v pořadí:

- Soubory, které <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> odpovídají `TRUSTED_PLATFORM_ASSEMBLIES` (po odebrání přípon souborů).
- Soubory sestavení nativní bitové kopie v `APP_NI_PATHS` nástroji s běžnými příponami souborů.
- Soubory sestavení v `APP_PATHS` nástroji s běžnými příponami souborů.

## <a name="satellite-resource-assembly-probing"></a>Satelitní zjišťování sestavení (prostředků)

Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, Sestavte sadu cest k souborům.

Pro každou cestu v `PLATFORM_RESOURCE_ROOTS` a potom `APP_PATHS` přidejte <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> řetězec, oddělovač adresáře, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> řetězec a příponu. dll.

Pokud existuje libovolný vyhovující soubor, pokuste se ho načíst a vrátit.

## <a name="unmanaged-native-library-probing"></a>Nespravované (nativní) knihovny Bingu

Když zjistíte, že zjišťování nespravované knihovny najde, `NATIVE_DLL_SEARCH_DIRECTORIES` prohledávají se hledání vyhovující knihovny.
