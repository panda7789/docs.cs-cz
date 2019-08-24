---
title: Algoritmus načítání spravovaného sestavení – .NET Core
description: Popis podrobností algoritmu načítání spravovaného sestavení v rozhraní .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: f368e2c20039f8679186a8d806850c9c92be8d3a
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017335"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmus načítání spravovaného sestavení

Spravovaná sestavení se nacházejí a načítají pomocí algoritmu zahrnujícího různé fáze.

Všechna spravovaná sestavení s výjimkou satelitních sestavení a `WinRT` sestavení používají stejný algoritmus.

## <a name="when-are-managed-assemblies-loaded"></a>Kdy jsou spravovaná sestavení načtena?

Nejběžnějším mechanismem pro aktivaci spravovaného zatížení sestavení je statický odkaz na sestavení. Tyto odkazy jsou vloženy kompilátorem vždy, když kód používá typ definovaný v jiném sestavení. Tato sestavení jsou načtena`load-by-name`() podle potřeby modulem runtime.

Přímé použití specifických rozhraní API také spustí načítání:

|rozhraní API  |Popis  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Načtení z cesty|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Načíst z objektu.|[Tato](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Načtení z cesty v nové <xref:System.Runtime.Loader.AssemblyLoadContext> instanci|Nová <xref:System.Runtime.Loader.AssemblyLoadContext> instance.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Načtení z cesty v <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instanci.<p>Přidá obslužnou rutinu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>do. <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> Obslužná rutina načte závislosti sestavení z jeho adresáře.|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Instance.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Načíst z objektu.|Odvozeno od volajícího.<p>Preferovat <xref:System.Runtime.Loader.AssemblyLoadContext> metody.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody`assemblyResolver` pomocí argumentu.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Pokud typ `name` popisuje kvalifikovaný obecný typ sestavení, Trigger a `Load-by-name`.|Odvozeno od volajícího.<p>Preferovat <xref:System.Type.GetType%2A?displayProperty=nameWithType> při použití kvalifikovaného typu názvů sestavení.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Odvozeno od volajícího.<p>Dáváte <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> přednost metodám, <xref:System.Type> které přebírají argument.|

## <a name="algorithm"></a>Algoritmus

Následující algoritmus popisuje, jak modul runtime načítá spravované sestavení.

1. `active` Určete .<xref:System.Runtime.Loader.AssemblyLoadContext>

    - Pro statický odkaz na `active` <xref:System.Runtime.Loader.AssemblyLoadContext> sestavení je instance, která načte odkazované sestavení.
    - Upřednostňovaná rozhraní API `active` vytvářejí <xref:System.Runtime.Loader.AssemblyLoadContext> explicitní.
    - Další rozhraní API odvozují `active`. <xref:System.Runtime.Loader.AssemblyLoadContext> Pro tato rozhraní API <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> se použije vlastnost. Pokud je `null`jeho hodnota, použije se <xref:System.Runtime.Loader.AssemblyLoadContext> odvozená instance.
    - Viz tabulka výše.

2. Pro metody aktivní <xref:System.Runtime.Loader.AssemblyLoadContext> načte sestavení. `Load-by-name` V pořadí podle priority podle:
    * Probíhá kontrola `cache-by-name`.

    * <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> Volání funkce.

    * Kontroluje se <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> mezipaměť instancí a spouští se [výchozí logika pro zjišťování spravovaného sestavení](default-probing.md#managed-assembly-default-probing) .

    * Vyvolává se <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> událost pro aktivní AssemblyLoadContext.

    * Vyvolává se <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.

3. Pro ostatní typy zatížení `active` <xref:System.Runtime.Loader.AssemblyLoadContext> načte sestavení. V pořadí podle priority podle:
    * Probíhá kontrola `cache-by-name`.

    * Načítání ze zadané cesty nebo nezpracovaného objektu sestavení.

4. V obou případech, pokud je sestavení nově načteno, pak:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Událost je vyvolána.
   - Odkaz je přidán do <xref:System.Runtime.Loader.AssemblyLoadContext> `cache-by-name`instance sestavení.

5. Pokud je sestavení nalezeno, odkaz je přidán podle potřeby `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance `cache-by-name`.
