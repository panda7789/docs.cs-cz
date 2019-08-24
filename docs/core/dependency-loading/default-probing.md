---
title: Výchozí zjišťování – .NET Core
description: Přehled logiky zjišťování pro <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> .NET Core pro vyhledání závislostí.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 020b1d0342ae822021905d2e749037f45031eb22
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017344"
---
# <a name="default-probing"></a>Výchozí zjišťování

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Instance zodpovídá za vyhledání závislostí sestavení. Tento článek popisuje <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logiku probingu instance.

## <a name="host-configured-probing-properties"></a>Vlastnosti služby probingu konfigurované pro hostitele

Po spuštění modulu runtime poskytuje hostitel modulu runtime sadu pojmenovaných vlastností Bingu, které konfigurují <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cesty testu paměti.

Každá vlastnost probingu je volitelná.  Pokud je tato vlastnost k dispozici, je hodnota řetězce, která obsahuje oddělený seznam absolutních cest. Oddělovač je '; ' ve Windows a ': ' na všech ostatních platformách.

|Název vlastnosti                 |Popis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Seznam cest k souborům sestavení platformy a aplikace |
|`PLATFORM_RESOURCE_ROOTS`       | Seznam cest k adresářům pro hledání satelitních sestavení prostředků |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Seznam cest adresáře, ve kterých se mají hledat nespravované (nativní) knihovny.        |
|`APP_PATHS`                     | Seznam cest adresáře, ve kterých se mají vyhledávat spravovaná sestavení |
|`APP_NI_PATHS`                  | Seznam cest adresáře, ve kterých se mají vyhledávat nativní bitové kopie spravovaných sestavení |

### <a name="how-are-the-properties-populated"></a>Jak se naplní vlastnosti?

Existují dva hlavní scénáře pro naplnění vlastností podle toho, zda `<myapp>.deps.json` soubor existuje.

- Když je `*.deps.json` soubor přítomen, analyzuje se a naplní vlastnosti probingu.
- `*.deps.json` Pokud soubor neexistuje, předpokládá se, že adresář aplikace obsahuje všechny závislosti. Obsah adresáře slouží k naplnění vlastností probingu.

Kromě toho `*.deps.json` jsou soubory pro všechny odkazované architektury podobně analyzovány.

Nakonec můžete k přidání `ADDITIONAL_DEPS` dalších závislostí použít proměnnou prostředí.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Návody zobrazit vlastnosti zjišťování ze spravovaného kódu?

Jednotlivé vlastnosti jsou k dispozici voláním <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkce s názvem vlastnosti z tabulky výše.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Návody ladit konstrukci vlastností probingu?

Hostitel modulu runtime .NET Core bude výstupem užitečných zpráv trasování, když jsou povolené určité proměnné prostředí:

|Proměnná prostředí        |Popis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Povolí trasování.|
|`COREHOST_TRACEFILE=<path>` |Vykreslí místo výchozího `stderr`umístění cestu k souboru.|
|`COREHOST_TRACE_VERBOSITY`  |Nastaví podrobnost z hodnoty 1 (nejnižší) na 4 (nejvyšší).|

## <a name="managed-assembly-default-probing"></a>Výchozí zjišťování spravovaného sestavení

Když zjistíte, že <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zjišťování má spravované sestavení, vypadá v pořadí:
- Soubory, které <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` odpovídají (po odebrání přípon souborů).
- Soubory sestavení nativní bitové kopie `APP_NI_PATHS` v nástroji s běžnými příponami souborů.
- Soubory sestavení v `APP_PATHS` nástroji s běžnými příponami souborů.

## <a name="satellite-resource-assembly-probing"></a>Satelitní zjišťování sestavení (prostředků)

Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, Sestavte sadu cest k souborům.

Pro každou cestu v `PLATFORM_RESOURCE_ROOTS` a potom `APP_PATHS`přidejte <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> řetězec, oddělovač adresáře, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> řetězec a příponu. dll.

Pokud existuje libovolný vyhovující soubor, pokuste se ho načíst a vrátit.

## <a name="unmanaged-native-library-probing"></a>Nespravované (nativní) knihovny Bingu

Když zjistíte, že `NATIVE_DLL_SEARCH_DIRECTORIES` zjišťování nespravované knihovny najde, prohledávají se hledání vyhovující knihovny,
