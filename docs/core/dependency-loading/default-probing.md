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
# <a name="default-probing"></a>Výchozí zjišťování

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> je zodpovědná za vyhledání závislostí sestavení. Tento článek popisuje <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logiku zjišťování instance.

## <a name="host-configured-probing-properties"></a>Vlastnosti zjišťování nakonfigurované hostitelem

Při spuštění runtime hostitel runtime poskytuje sadu pojmenovaných vlastností <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zjišťování, které konfigurují cesty promoru.

Každá vlastnost zjišťování je volitelná. Pokud je k dispozici, každá vlastnost je řetězcová hodnota, která obsahuje oddělený seznam absolutních cest. Oddělovač je ';' v systému Windows a ':' na všech ostatních platformách.

|Název vlastnosti                 |Popis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Seznam cest souborů sestavení platformy a aplikace. |
|`PLATFORM_RESOURCE_ROOTS`       | Seznam cest adresářů pro vyhledávání satelitních sestavení prostředků. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Seznam cest adresářů pro vyhledávání nespravovaných (nativních) knihoven.        |
|`APP_PATHS`                     | Seznam cest adresáře pro vyhledávání spravovaných sestavení. |
|`APP_NI_PATHS`                  | Seznam cest adresáře pro vyhledávání nativních bitových kopií spravovaných sestavení. |

### <a name="how-are-the-properties-populated"></a>Jak jsou vlastnosti naplněny?

Existují dva hlavní scénáře pro vyplnění vlastnosti v závislosti na tom, zda existuje soubor * \<myapp>.deps.json.*

- Pokud je soubor * \*.deps.json* přítomen, je analyzován k naplnění vlastností zjišťování.
- Pokud soubor * \*.deps.json* není k dispozici, předpokládá se, že adresář aplikace obsahuje všechny závislosti. Obsah adresáře se používá k naplnění vlastností zjišťování.

Kromě toho * \*jsou* podobně analyzovány soubory .deps.json pro všechny odkazované architektury.

Nakonec proměnné `ADDITIONAL_DEPS` prostředí lze přidat další závislosti.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Jak zobrazím vlastnosti zjišťování ze spravovaného kódu?

Každá vlastnost je k <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> dispozici voláním funkce s názvem vlastnosti z výše uvedené tabulky.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Jak lze ladit konstrukci vlastností sondování?

Hostitel runtime .NET Core bude výstupem užitečných trasovacích zpráv, pokud jsou povoleny určité proměnné prostředí:

|Proměnná prostředí        |Popis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Povolí trasování.|
|`COREHOST_TRACEFILE=<path>` |Trasování na cestu k souboru namísto výchozí `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Nastaví podrobnost z 1 (nejnižší) na 4 (nejvyšší).|

## <a name="managed-assembly-default-probing"></a>Výchozí zjišťování spravovaného sestavení

Při zjišťování najít spravované sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> vypadá v pořadí na adrese:

- Soubory odpovídající <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` in (po odebrání přípony souborů).
- Nativní soubory `APP_NI_PATHS` sestavení obrazu s běžnými příponami souborů.
- Soubory sestavení `APP_PATHS` v s běžnými příponami souborů.

## <a name="satellite-resource-assembly-probing"></a>Satelitní (zdroj) zjišťování sestavení

Chcete-li najít satelitní sestavení pro konkrétní jazykovou verzi, vytvořte sadu cest souborů.

Pro každou `PLATFORM_RESOURCE_ROOTS` cestu `APP_PATHS`v a <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> potom připojit řetězec, oddělovač adresářů, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> řetězec a rozšíření '.dll'.

Pokud existuje nějaký odpovídající soubor, pokuste se jej načíst a vrátit.

## <a name="unmanaged-native-library-probing"></a>Nespravované (nativní) sondování knihovny

Při zjišťování vyhledat nespravované knihovny, `NATIVE_DLL_SEARCH_DIRECTORIES` jsou prohledány hledá odpovídající knihovny.
