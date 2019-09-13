---
title: Principy AssemblyLoadContext – .NET Core
description: Klíčové koncepty pro pochopení účelu a chování AssemblyLoadContext v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 429f8145e4462cfa93bf286fd35b39f58f9afa64
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926373"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Principy System. Runtime. Loader. AssemblyLoadContext

<xref:System.Runtime.Loader.AssemblyLoadContext> Třída je jedinečná pro .NET Core. Tento článek se pokusí doplnit <xref:System.Runtime.Loader.AssemblyLoadContext> dokumentaci k rozhraní API o koncepční informace.

Tento článek je relevantní pro vývojáře implementující dynamické načítání, zejména pro vývojáře architektury dynamického nasazování.

## <a name="what-is-the-assemblyloadcontext"></a>Co je AssemblyLoadContext?

Každá aplikace .NET Core implicitně používá <xref:System.Runtime.Loader.AssemblyLoadContext>.
Je poskytovatelem modulu runtime pro vyhledání a načtení závislostí. Pokaždé, když se načte závislost <xref:System.Runtime.Loader.AssemblyLoadContext> , vyvolá se instance, která ji najde.

- Poskytuje službu pro hledání, načítání a ukládání spravovaných sestavení a dalších závislostí do mezipaměti.

- Aby bylo možné podporovat dynamické načítání a uvolňování kódu, vytvoří izolovaný kontext pro načítání kódu a jeho závislostí <xref:System.Runtime.Loader.AssemblyLoadContext> ve své vlastní instanci.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Pokud potřebujete více instancí AssemblyLoadContext?

Jedna <xref:System.Runtime.Loader.AssemblyLoadContext> instance je omezena na načtení přesně jedné verze <xref:System.Reflection.Assembly> jednoduchého názvu <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>sestavení.

Toto omezení může být problém při dynamickém načítání modulů kódu. Každý modul je nezávisle zkompilován a může záviset na různých <xref:System.Reflection.Assembly>verzích. K tomuto problému obvykle dochází, když různé moduly závisejí na různých verzích běžně používané knihovny.

Pro podporu dynamického načítání kódu <xref:System.Runtime.Loader.AssemblyLoadContext> rozhraní API poskytuje pro načítání konfliktních verzí <xref:System.Reflection.Assembly> nástroje ve stejné aplikaci. Každá <xref:System.Runtime.Loader.AssemblyLoadContext> instance poskytuje jedinečné mapování slovníku každého <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> konkrétní <xref:System.Reflection.Assembly> instance.

Poskytuje také pohodlný mechanismus pro seskupení závislostí souvisejících s modulem kódu pro pozdější uvolnění.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co je zvláštní informace o instanci AssemblyLoadContext. Default?

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> Instance je automaticky vyplněna modulem runtime při spuštění.  K vyhledání a vyhledání všech statických závislostí používá [výchozí zjišťování](default-probing.md) .

Řeší nejběžnější scénáře načítání závislostí.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Jak AssemblyLoadContext podporuje dynamické závislosti?

<xref:System.Runtime.Loader.AssemblyLoadContext>má různé události a virtuální funkce, které je možné přepsat.

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> Instance podporuje pouze přepsání událostí.

V článcích [spravovaný algoritmus pro načítání sestavení](loading-managed.md), [algoritmus načítání satelitních sestavení](loading-resources.md)a [nespravovaný (nativní) modul načítání knihovny](loading-unmanaged.md) odkazují na všechny dostupné události a virtuální funkce.  Články ukazují relativní pozici každé události a funkce v algoritmech načítání. V tomto článku nejsou tyto informace reprodukovány.

Tato část obsahuje obecné principy relevantních událostí a funkcí.

- **Být možné opakovat**. Dotaz na konkrétní závislost musí vždy mít stejnou odpověď. Musí být vrácena stejná instance načtené závislosti. Tento požadavek je zásadní pro konzistenci mezipaměti. Konkrétně pro spravovaná sestavení vytváříme <xref:System.Reflection.Assembly> mezipaměť. Klíč mezipaměti je jednoduchý název <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>sestavení.
- **Obvykle nevyvolejte**.  Je očekáváno, že tyto funkce `null` vrací místo throw, pokud nelze najít požadovanou závislost. K vyvolání dojde v předčasném ukončení hledání a k šíření výjimky pro volajícího. Vystavení by mělo být omezeno na neočekávané chyby, jako je poškozené sestavení nebo nedostatek paměti.
- **Vyhněte se rekurzi**. Počítejte s tím, že tyto funkce a obslužné rutiny implementují pravidla načítání pro hledání závislostí. Vaše implementace by neměla volat rozhraní API, která spouštějí rekurzi. Váš kód by měl obvykle volat funkce **AssemblyLoadContext** Load, které vyžadují specifickou cestu nebo argument odkazu na paměť.
- **Načtěte do správného AssemblyLoadContext**. Volba místa načtení závislostí je specifická pro aplikaci.  Tato volba je implementována těmito událostmi a funkcemi. Když váš kód volá funkce **AssemblyLoadContext** Load-by-Path, zavolejte je na instanci, kde chcete kód načíst. Při návratu `null` a <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> zanechání popisovače může být zátěž Nejjednodušší volbou.
- **Uvědomte si Races vlákna**. Načítání může být aktivováno více vlákny. AssemblyLoadContext zpracovává vlákna Races atomicky přidávání sestavení do mezipaměti. Instance rasy loser je zahozena. V logice implementace Nepřidávejte další logiku, která správně nezpracovává více vláken.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak jsou izolované dynamické závislosti?

Každá <xref:System.Runtime.Loader.AssemblyLoadContext> instance představuje jedinečný obor pro <xref:System.Reflection.Assembly> instance a <xref:System.Type> definice.

Mezi těmito závislostmi neexistuje žádná binární izolace. Jsou izolované jenom tím, že se nehledají podle názvu.

V každém <xref:System.Runtime.Loader.AssemblyLoadContext>z těchto:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>může odkazovat na jinou <xref:System.Reflection.Assembly> instanci.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>může vrátit jinou instanci typu pro stejný typ `name`.

## <a name="how-are-dependencies-shared"></a>Jak se sdílí závislosti?

Mezi <xref:System.Runtime.Loader.AssemblyLoadContext> instancemi je možné snadno sdílet závislosti. Obecný model je určen pro <xref:System.Runtime.Loader.AssemblyLoadContext> načtení závislosti.  Druhá sdílí závislost pomocí odkazu na načtené sestavení.

Toto sdílení je vyžadováno pro sestavení modulu runtime. Tato sestavení lze načíst pouze do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Stejný je vyžadován pro architektury, jako `ASP.NET`, `WPF`nebo `WinForms`.

Doporučuje se, aby se sdílené závislosti načetly <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>do. Toto sdílení je běžným vzorem návrhu.

Sdílení je implementováno v kódování vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> instance. <xref:System.Runtime.Loader.AssemblyLoadContext>má různé události a virtuální funkce, které je možné přepsat. Když kterákoli z těchto funkcí vrátí odkaz na <xref:System.Reflection.Assembly> instanci, která byla načtena do jiné <xref:System.Runtime.Loader.AssemblyLoadContext> instance, <xref:System.Reflection.Assembly> je instance sdílena. Algoritmus standardního zatížení se odkládá na <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> načítání pro zjednodušení společného vzoru sdílení.  Viz [algoritmus načítání spravovaného sestavení](loading-managed.md).

## <a name="complications"></a>Komplikace

### <a name="type-conversion-issues"></a>Problémy s převodem typu

Pokud dvě <xref:System.Runtime.Loader.AssemblyLoadContext> instance obsahují definice typu se stejným `name`typem, nejsou stejného typu. Jsou stejného typu, pokud jsou a pouze v případě, že pocházejí ze <xref:System.Reflection.Assembly> stejné instance.

Chcete-li zkomplikovat otázky, zprávy o výjimce týkající se těchto neodpovídajících typů mohou být matoucí. Typy jsou odkazovány na zprávy výjimek podle jejich jednoduchého typu. Zpráva o běžné výjimce v tomto případě by měla být ve tvaru:

```
Object of type 'IsolatedType' cannot be converted to type 'IsolatedType'.
```

### <a name="debugging-type-conversion-issues"></a>Problémy s převodem typu ladění

Vzhledem k dvojici neodpovídajících typů je důležité také znát:

- Každý typ<xref:System.Type.Assembly?displayProperty=nameWithType>
- Každý typ <xref:System.Runtime.Loader.AssemblyLoadContext>, který lze získat <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> prostřednictvím funkce.

Vzhledem k dvěma `a` objektům a `b`vyhodnocení následujícího v ladicím programu bude užitečné:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Řešení problémů s převodem typů

Existují dva vzory návrhu pro řešení těchto problémů s převodem typů.

1. Použijte běžné sdílené typy. Tento sdílený typ může být buď primitivní typ modulu runtime, nebo může zahrnovat vytvoření nového sdíleného typu ve sdíleném sestavení.  Sdílený typ je často [rozhraní](../../csharp/language-reference/keywords/interface.md) definované v sestavení aplikace. Viz také: [Jak se sdílí závislosti?](#how-are-dependencies-shared)

2. Použijte techniky zařazování pro převod z jednoho typu na jiný.
