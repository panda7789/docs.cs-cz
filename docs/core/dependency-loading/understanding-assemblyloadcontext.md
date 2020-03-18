---
title: Principy AssemblyLoadContext - .NET Core
description: Klíčové koncepty pochopit účel a chování AssemblyLoadContext v .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72291259"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Principy System.Runtime.Loader.AssemblyLoadContext

Třída <xref:System.Runtime.Loader.AssemblyLoadContext> je jedinečná pro .NET Core. Tento článek se pokusí <xref:System.Runtime.Loader.AssemblyLoadContext> doplnit dokumentaci rozhraní API s koncepční informace.

Tento článek je relevantní pro vývojáře, kteří implementují dynamické načítání, zejména vývojáři architektury dynamického načítání.

## <a name="what-is-the-assemblyloadcontext"></a>Co je AssemblyLoadContext?

Každá aplikace .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext>implicitně používá rozhraní .
Je to zprostředkovatel za běhu pro vyhledávání a načítání závislostí. Při každém načtení závislosti <xref:System.Runtime.Loader.AssemblyLoadContext> je vyvolána instance k jeho vyhledání.

- Poskytuje službu vyhledání, načítání a ukládání do mezipaměti spravovaných sestavení a dalších závislostí.

- Pro podporu dynamickénačítání kódu a uvolnění vytvoří izolovaný kontext pro načítání kódu <xref:System.Runtime.Loader.AssemblyLoadContext> a jeho závislosti v jejich vlastní instanci.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Kdy potřebujete více instancí AssemblyLoadContext?

Jedna <xref:System.Runtime.Loader.AssemblyLoadContext> instance je omezena na načtení <xref:System.Reflection.Assembly> přesně jedné <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>verze na jednoduchý název sestavení .

Toto omezení se může stát problémpři dynamickém načítání modulů kódu. Každý modul je zkompilován nezávisle a může <xref:System.Reflection.Assembly>záviset na různých verzích rozhraní . K tomuto problému obvykle dochází, když různé moduly závisí na různých verzích běžně používané knihovny.

Pro podporu dynamického <xref:System.Runtime.Loader.AssemblyLoadContext> načítání kódu poskytuje rozhraní API pro <xref:System.Reflection.Assembly> načítání konfliktních verzí ve stejné aplikaci. Každá <xref:System.Runtime.Loader.AssemblyLoadContext> instance poskytuje jedinečný slovník <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> mapování <xref:System.Reflection.Assembly> každý na konkrétní instanci.

Poskytuje také pohodlný mechanismus pro seskupení závislostí souvisejících s modulkódu pro pozdější uvolnění.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co je zvláštního na instanci AssemblyLoadContext.Default?

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> je automaticky naplněna runtime při spuštění.  Používá [výchozí zjišťování](default-probing.md) k vyhledání a vyhledání všech statických závislostí.

Řeší nejběžnější scénáře načítání závislostí.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Jak AssemblyLoadContext podporuje dynamické závislosti?

<xref:System.Runtime.Loader.AssemblyLoadContext>má různé události a virtuální funkce, které mohou být přepsány.

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> podporuje pouze přepsání událostí.

Články [Algoritmus načítání spravovaného sestavení](loading-managed.md), [Algoritmus načítání satelitního sestavení](loading-resources.md)a [Algoritmus načítání nespravované (nativní) knihovny](loading-unmanaged.md) odkazují na všechny dostupné události a virtuální funkce.  Články ukazují relativní pozici každé události a funkce v algoritmech načítání. Tento článek tyto informace nereprodukuje.

Tento oddíl se zabývá obecnými zásadami příslušných událostí a funkcí.

- **Být opakovatelný**. Dotaz na určitou závislost musí vždy vést ke stejné odpovědi. Musí být vrácena stejná instancí načtené závislosti. Tento požadavek je zásadní pro konzistenci mezipaměti. Zejména pro spravovaná sestavení vytváříme <xref:System.Reflection.Assembly> mezipaměť. Klíč mezipaměti je jednoduchý <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>název sestavení .
- **Obvykle neházejte**.  Očekává se, že tyto `null` funkce vrátit spíše než vyvolat, když nelze najít požadovanou závislost. Vyvolání předčasně ukončí hledání a bude šířit výjimku volajícího. Vyvolání by měla být omezena na neočekávané chyby, jako je poškozené sestavení nebo podmínku nedostatku paměti.
- **Vyhněte se rekurzi**. Uvědomte si, že tyto funkce a obslužné rutiny implementovat pravidla načítání pro vyhledání závislostí. Implementace by neměla volat api, která aktivují rekurzi. Váš kód by měl obvykle volat **AssemblyLoadContext** načíst funkce, které vyžadují konkrétní cestu nebo referenční argument paměti.
- **Načtěte do správné assemblyloadcontext**. Volba, kde načíst závislosti je specifické pro aplikaci.  Volba je implementována těmito událostmi a funkcemi. Když váš kód volá **AssemblyLoadContext** load-by-path funkce volat na instanci, kde chcete kód načten. Někdy se `null` vrací a <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> nechat zvládnout zatížení může být nejjednodušší volbou.
- **Buďte si vědomi závitových závodů**. Načítání může být spuštěno více vlákny. AssemblyLoadContext zpracovává závody vláken atomicky přidáním sestavení do mezipaměti. Instance poraženého závodu je zahozena. V logice implementace nepřidávejte další logiku, která nezpracovává více vláken správně.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak jsou dynamické závislosti izolovány?

Každá <xref:System.Runtime.Loader.AssemblyLoadContext> instance představuje jedinečný <xref:System.Reflection.Assembly> obor <xref:System.Type> pro instance a definice.

Neexistuje žádná binární izolace mezi těmito závislostmi. Jsou izolováni jen tím, že se nenajdou podle jména.

V <xref:System.Runtime.Loader.AssemblyLoadContext>každém :

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>může odkazovat <xref:System.Reflection.Assembly> na jinou instanci.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>může vrátit jiný typ instance `name`pro stejný typ .

## <a name="how-are-dependencies-shared"></a>Jak jsou závislosti sdíleny?

Závislosti lze snadno sdílet <xref:System.Runtime.Loader.AssemblyLoadContext> mezi instancemi. Obecný model je <xref:System.Runtime.Loader.AssemblyLoadContext> pro jeden načíst závislost.  Ostatní sdílí závislost pomocí odkazu na načtené sestavení.

Toto sdílení je vyžadováno pro sestavení za běhu. Tato sestavení lze načíst <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>pouze do . Totéž platí pro rámce `ASP.NET` `WPF`jako `WinForms`, , nebo .

Doporučuje se, aby sdílené závislosti byly <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>načteny do aplikace . Toto sdílení je běžný návrhový vzor.

Sdílení je implementováno v <xref:System.Runtime.Loader.AssemblyLoadContext> kódování vlastní instance. <xref:System.Runtime.Loader.AssemblyLoadContext>má různé události a virtuální funkce, které mohou být přepsány. Pokud některá z těchto funkcí <xref:System.Reflection.Assembly> vrátí odkaz na <xref:System.Runtime.Loader.AssemblyLoadContext> instanci, která byla načtena v jiné <xref:System.Reflection.Assembly> instanci, je instance sdílena. Standardní algoritmus zatížení <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> odkládá pro načítání zjednodušit společný vzor sdílení.  Viz [Algoritmus načítání spravovaného sestavení](loading-managed.md).

## <a name="complications"></a>Komplikace

### <a name="type-conversion-issues"></a>Problémy s převodem typu

Pokud <xref:System.Runtime.Loader.AssemblyLoadContext> dvě instance obsahují definice typů `name`se stejným , nejsou stejného typu. Jsou stejného typu, pokud a pouze v <xref:System.Reflection.Assembly> případě, že pocházejí ze stejné instance.

Chcete-li věci zkomplikovat, zprávy o výjimkách o těchto neodpovídajících typů může být matoucí. Typy jsou uvedeny ve zprávách výjimek jejich jednoduché názvy typů. Společná zpráva o výjimce v tomto případě by byla ve formě:

> Objekt typu IsolatedType nelze převést na typ "IsolatedType".

### <a name="debugging-type-conversion-issues"></a>Problémy s převodem typu ladění

Vzhledem k tomu, pár neodpovídající typy je důležité také vědět:

- Každý typ je<xref:System.Type.Assembly?displayProperty=nameWithType>
- Každý typ <xref:System.Runtime.Loader.AssemblyLoadContext>, který lze získat <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> prostřednictvím funkce.

Vzhledem `a` k `b`tomu, dva objekty a , vyhodnocení následující v ladicím programu bude užitečné:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Řešení problémů s převodem typu

Existují dva návrhové vzory pro řešení těchto problémů převodu typu.

1. Používejte běžné sdílené typy. Tento sdílený typ může být buď primitivní typ runtime, nebo může zahrnovat vytvoření nového sdíleného typu ve sdíleném sestavení.  Často sdílený typ je [rozhraní](../../csharp/language-reference/keywords/interface.md) definované v sestavení aplikace. Viz také: [Jak jsou sdílené závislosti?](#how-are-dependencies-shared).

2. Pomocí zařazovacích technik můžete převést z jednoho typu na jiný.
