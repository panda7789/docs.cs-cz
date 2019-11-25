---
title: Algoritmus načítání spravovaného sestavení – .NET Core
description: Popis podrobností algoritmu načítání spravovaného sestavení v rozhraní .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973502"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmus načítání spravovaného sestavení

Spravovaná sestavení se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.

Všechna spravovaná sestavení s výjimkou satelitních sestavení a `WinRT` sestavení používají stejný algoritmus.

## <a name="when-are-managed-assemblies-loaded"></a>Kdy jsou spravovaná sestavení načtena?

Nejběžnějším mechanismem pro aktivaci spravovaného zatížení sestavení je statický odkaz na sestavení. Tyto odkazy jsou vloženy kompilátorem vždy, když kód používá typ definovaný v jiném sestavení. Tato sestavení jsou načtena (`load-by-name`) podle potřeby modulem runtime.

Přímé použití specifických rozhraní API také spustí načítání:

|rozhraní API  |Popis  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Načtení z cesty|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Načíst z objektu.|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Načtení z cesty v nové instanci <xref:System.Runtime.Loader.AssemblyLoadContext>|Nová instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Načtení z cesty v instanci <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.<p>Přidá obslužnou rutinu <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> k <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. Obslužná rutina načte závislosti sestavení z jeho adresáře.|Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Načtení z objektu v nové instanci <xref:System.Runtime.Loader.AssemblyLoadContext>.|Nová instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody pomocí argumentu `assemblyResolver`.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Pokud typ `name` popisuje kvalifikovaný obecný typ sestavení, aktivujte `Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Type.GetType%2A?displayProperty=nameWithType> při použití kvalifikovaného názvu typu sestavení.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Dáváte přednost <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metodám, které přebírají argument <xref:System.Type>.|

## <a name="algorithm"></a>Algoritmus

Následující algoritmus popisuje, jak modul runtime načítá spravované sestavení.

1. Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.

    - Pro statický odkaz na sestavení je `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance, která načte odkazující sestavení.
    - Upřednostňovaná rozhraní API nastaví `active` <xref:System.Runtime.Loader.AssemblyLoadContext> explicitní.
    - Jiná rozhraní API odvozují `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Pro tato rozhraní API se použije vlastnost <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType>. Je-li jeho hodnota `null`, je použita odvozená instance <xref:System.Runtime.Loader.AssemblyLoadContext>.
    - Viz tabulka výše.

2. Pro `Load-by-name` metody načte aktivní <xref:System.Runtime.Loader.AssemblyLoadContext> sestavení. V pořadí podle priority podle:
    - Probíhá kontrola `cache-by-name`.

    - Volání funkce <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.

    - Kontroluje se mezipaměť instancí <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> a spouští se [výchozí logika pro zjišťování spravovaného sestavení](default-probing.md#managed-assembly-default-probing) .

    - Vyvolává se událost <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> pro aktivní AssemblyLoadContext.

    - Vyvolává se událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

3. Pro ostatní typy načtení `active` <xref:System.Runtime.Loader.AssemblyLoadContext> načte sestavení. V pořadí podle priority podle:
    - Probíhá kontrola `cache-by-name`.

    - Načítání ze zadané cesty nebo nezpracovaného objektu sestavení.

4. V obou případech, pokud je sestavení nově načteno, pak:
   - Vyvolá se událost <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType>.
   - Do `cache-by-name`<xref:System.Runtime.Loader.AssemblyLoadContext> instance sestavení se přidá odkaz.

5. Pokud je sestavení nalezeno, přidá se podle potřeby odkaz na `cache-by-name`instance `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.
