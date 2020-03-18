---
title: Algoritmus načítání spravovaného sestavení - .NET Core
description: Popis podrobností algoritmu načítání spravovaného sestavení v rozhraní .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973502"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmus načítání spravovaného sestavení

Spravovaná sestavení jsou umístěna a načtena s algoritmem zahrnujícím různé fáze.

Všechna spravovaná sestavení `WinRT` s výjimkou satelitních sestavení a sestavení používají stejný algoritmus.

## <a name="when-are-managed-assemblies-loaded"></a>Kdy jsou načtena spravovaná sestavení?

Nejběžnější mechanismus pro aktivaci zatížení spravované sestavení je odkaz statické sestavení. Tyto odkazy jsou vloženy kompilátorem vždy, když kód používá typ definovaný v jiném sestavení. Tato sestavení jsou`load-by-name`načtena ( ) podle potřeby za běhu.

Přímé použití konkrétních rozhraní API také spustí zatížení:

|Rozhraní API  |Popis  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|V [této](../../csharp/language-reference/keywords/this.md) instanci.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Načíst z cesty.|V [této](../../csharp/language-reference/keywords/this.md) instanci.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Načíst z objektu.|V [této](../../csharp/language-reference/keywords/this.md) instanci.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Načíst z cesty <xref:System.Runtime.Loader.AssemblyLoadContext> v nové instanci|Nová <xref:System.Runtime.Loader.AssemblyLoadContext> instance.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Načíst z <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cesty v instanci.<p>Přidá <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> obslužnou rutinu do . <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Obslužná rutina načte závislosti sestavení z jeho adresáře.|Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferujte <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Načíst z objektu v nové <xref:System.Runtime.Loader.AssemblyLoadContext> instanci.|Nová <xref:System.Runtime.Loader.AssemblyLoadContext> instance.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferujte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody `assemblyResolver` s argumentem.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Pokud `name` typ popisuje obecný typ s `Load-by-name`kvalifikací sestavení, aktivuje .|Odvozeno od volajícího.<p>Preferovat <xref:System.Type.GetType%2A?displayProperty=nameWithType> při použití sestavení kvalifikovaných názvů typů.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferujte <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody <xref:System.Type> s argumentem.|

## <a name="algorithm"></a>Algoritmus

Následující algoritmus popisuje, jak runtime načte spravované sestavení.

1. Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.

    - Pro odkaz statické sestavení `active` <xref:System.Runtime.Loader.AssemblyLoadContext> je instance, která načetla odkazující sestavení.
    - Upřednostňovaná prostředí `active` <xref:System.Runtime.Loader.AssemblyLoadContext> API dávají explicitní.
    - Ostatní api odvodit `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Pro tato api <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> se používá vlastnost. Pokud je `null`jeho hodnota , <xref:System.Runtime.Loader.AssemblyLoadContext> pak se použije odvozená instance.
    - Viz tabulka výše.

2. Pro `Load-by-name` metody aktivní <xref:System.Runtime.Loader.AssemblyLoadContext> zatížení sestavy. V pořadí podle priority podle:
    - Kontrola jeho `cache-by-name`.

    - Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkce.

    - Kontrola mezipaměti <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instancí a spuštění výchozí logiky [zjišťování spravovaného sestavení.](default-probing.md#managed-assembly-default-probing)

    - Vyvolání <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> události pro aktivní AssemblyLoadContext.

    - Vyvolání <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> akce.

3. U ostatních typů zatížení `active` <xref:System.Runtime.Loader.AssemblyLoadContext> zatížení sestavu. V pořadí podle priority podle:
    - Kontrola jeho `cache-by-name`.

    - Načítání ze zadané cesty nebo nezpracovaného objektu sestavení.

4. V obou případech, pokud je sestavení nově načteno, pak:
   - Událost <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> je vyvolána.
   - Odkaz je přidán do <xref:System.Runtime.Loader.AssemblyLoadContext> instance sestavení `cache-by-name`.

5. Pokud je sestavení nalezeno, je podle potřeby `active` <xref:System.Runtime.Loader.AssemblyLoadContext> přidán `cache-by-name`odkaz na instanci .
