---
title: Principy AssemblyLoadContext – .NET Core
description: Klíčové koncepty pro pochopení účelu a chování AssemblyLoadContext v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291259"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Principy System. Runtime. Loader. AssemblyLoadContext

Třída <xref:System.Runtime.Loader.AssemblyLoadContext> je jedinečná pro .NET Core. Tento článek se pokusí doplnit dokumentaci k rozhraní API @no__t 0 pomocí koncepčních informací.

Tento článek je relevantní pro vývojáře implementující dynamické načítání, zejména pro vývojáře architektury dynamického nasazování.

## <a name="what-is-the-assemblyloadcontext"></a>Co je AssemblyLoadContext?

Každá aplikace .NET Core implicitně používá <xref:System.Runtime.Loader.AssemblyLoadContext>.
Je poskytovatelem modulu runtime pro vyhledání a načtení závislostí. Pokaždé, když je načtena závislost, je vyvolána instance <xref:System.Runtime.Loader.AssemblyLoadContext> pro její vyhledání.

- Poskytuje službu pro hledání, načítání a ukládání spravovaných sestavení a dalších závislostí do mezipaměti.

- Aby bylo možné podporovat dynamické načítání a uvolňování kódu, vytvoří izolovaný kontext pro načítání kódu a jeho závislostí ve vlastní instanci <xref:System.Runtime.Loader.AssemblyLoadContext>.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Pokud potřebujete více instancí AssemblyLoadContext?

Jedna instance <xref:System.Runtime.Loader.AssemblyLoadContext> je omezena tak, aby se načetla přesně jedna verze <xref:System.Reflection.Assembly> na jednoduchý název sestavení, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.

Toto omezení může být problém při dynamickém načítání modulů kódu. Každý modul je nezávisle zkompilován a může záviset na různých verzích <xref:System.Reflection.Assembly>. K tomuto problému obvykle dochází, když různé moduly závisejí na různých verzích běžně používané knihovny.

Aby bylo možné podporovat dynamické načítání kódu, rozhraní API <xref:System.Runtime.Loader.AssemblyLoadContext> poskytuje k načítání konfliktních verzí <xref:System.Reflection.Assembly> ve stejné aplikaci. Každá instance <xref:System.Runtime.Loader.AssemblyLoadContext> poskytuje jedinečný slovník mapování každého <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> na konkrétní instanci <xref:System.Reflection.Assembly>.

Poskytuje také pohodlný mechanismus pro seskupení závislostí souvisejících s modulem kódu pro pozdější uvolnění.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co je zvláštní informace o instanci AssemblyLoadContext. Default?

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> je automaticky vyplněna modulem runtime při spuštění.  K vyhledání a vyhledání všech statických závislostí používá [výchozí zjišťování](default-probing.md) .

Řeší nejběžnější scénáře načítání závislostí.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Jak AssemblyLoadContext podporuje dynamické závislosti?

<xref:System.Runtime.Loader.AssemblyLoadContext> má různé události a virtuální funkce, které lze přepsat.

Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> podporuje pouze přepsání událostí.

V článcích [spravovaný algoritmus pro načítání sestavení](loading-managed.md), [algoritmus načítání satelitních sestavení](loading-resources.md)a [nespravovaný (nativní) modul načítání knihovny](loading-unmanaged.md) odkazují na všechny dostupné události a virtuální funkce.  Články ukazují relativní pozici každé události a funkce v algoritmech načítání. V tomto článku nejsou tyto informace reprodukovány.

Tato část obsahuje obecné principy relevantních událostí a funkcí.

- **Být možné opakovat**. Dotaz na konkrétní závislost musí vždy mít stejnou odpověď. Musí být vrácena stejná instance načtené závislosti. Tento požadavek je zásadní pro konzistenci mezipaměti. Konkrétně pro spravovaná sestavení vytváříme mezipaměť <xref:System.Reflection.Assembly>. Klíč mezipaměti je jednoduchý název sestavení <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.
- **Obvykle nevyvolejte**.  Očekává se, že tyto funkce vrací `null` namísto vyvolání, pokud se nepodaří najít požadovanou závislost. K vyvolání dojde v předčasném ukončení hledání a k šíření výjimky pro volajícího. Vystavení by mělo být omezeno na neočekávané chyby, jako je poškozené sestavení nebo nedostatek paměti.
- **Vyhněte se rekurzi**. Počítejte s tím, že tyto funkce a obslužné rutiny implementují pravidla načítání pro hledání závislostí. Vaše implementace by neměla volat rozhraní API, která spouštějí rekurzi. Váš kód by měl obvykle volat funkce **AssemblyLoadContext** Load, které vyžadují specifickou cestu nebo argument odkazu na paměť.
- **Načtěte do správného AssemblyLoadContext**. Volba místa načtení závislostí je specifická pro aplikaci.  Tato volba je implementována těmito událostmi a funkcemi. Když váš kód volá funkce **AssemblyLoadContext** Load-by-Path, zavolejte je na instanci, kde chcete kód načíst. Při návratu `null` a umožnění rutiny <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> může být zátěž nejjednodušším parametrem.
- **Uvědomte si Races vlákna**. Načítání může být aktivováno více vlákny. AssemblyLoadContext zpracovává vlákna Races atomicky přidávání sestavení do mezipaměti. Instance rasy loser je zahozena. V logice implementace Nepřidávejte další logiku, která správně nezpracovává více vláken.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak jsou izolované dynamické závislosti?

Každá instance <xref:System.Runtime.Loader.AssemblyLoadContext> představuje jedinečný rozsah pro instance <xref:System.Reflection.Assembly> a definice <xref:System.Type>.

Mezi těmito závislostmi neexistuje žádná binární izolace. Jsou izolované jenom tím, že se nehledají podle názvu.

V každém <xref:System.Runtime.Loader.AssemblyLoadContext>:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> se může vztahovat na jinou instanci <xref:System.Reflection.Assembly>.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType> může vracet jinou instanci typu pro stejný typ `name`.

## <a name="how-are-dependencies-shared"></a>Jak se sdílí závislosti?

Závislosti lze snadno sdílet mezi instancemi @no__t 0. Obecný model je pro jednu <xref:System.Runtime.Loader.AssemblyLoadContext> pro načtení závislosti.  Druhá sdílí závislost pomocí odkazu na načtené sestavení.

Toto sdílení je vyžadováno pro sestavení modulu runtime. Tato sestavení lze načíst pouze do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Totéž platí pro rozhraní, jako `ASP.NET`, `WPF` nebo `WinForms`.

Doporučuje se, aby se sdílené závislosti načetly do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Toto sdílení je běžným vzorem návrhu.

Sdílení je implementováno v kódování vlastní instance <xref:System.Runtime.Loader.AssemblyLoadContext>. <xref:System.Runtime.Loader.AssemblyLoadContext> má různé události a virtuální funkce, které lze přepsat. Když kterákoli z těchto funkcí vrátí odkaz na instanci <xref:System.Reflection.Assembly>, která byla načtena do jiné instance <xref:System.Runtime.Loader.AssemblyLoadContext>, je sdílena instance <xref:System.Reflection.Assembly>. Algoritmus Standard Load se po načtení ne<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> pro zjednodušení společného vzoru sdílení.  Viz [algoritmus načítání spravovaného sestavení](loading-managed.md).

## <a name="complications"></a>Komplikace

### <a name="type-conversion-issues"></a>Problémy s převodem typu

Pokud dvě instance <xref:System.Runtime.Loader.AssemblyLoadContext> obsahují definice typu se stejnou `name`, nejedná se o stejný typ. Jsou stejného typu, pokud jsou a pouze v případě, že pocházejí ze stejné instance <xref:System.Reflection.Assembly>.

Chcete-li zkomplikovat otázky, zprávy o výjimce týkající se těchto neodpovídajících typů mohou být matoucí. Typy jsou odkazovány na zprávy výjimek podle jejich jednoduchého typu. Zpráva o běžné výjimce v tomto případě by měla být ve tvaru:

> Objekt typu ' IsolatedType ' nelze převést na typ ' IsolatedType '.

### <a name="debugging-type-conversion-issues"></a>Problémy s převodem typu ladění

Vzhledem k dvojici neodpovídajících typů je důležité také znát:

- @No__t jednotlivých typů – 0
- Každý typ <xref:System.Runtime.Loader.AssemblyLoadContext>, který lze získat pomocí funkce <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType>.

Vzhledem k těmto dvěma objektům `a` a `b` bude užitečné vyhodnotit následující v ladicím programu:

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

1. Použijte běžné sdílené typy. Tento sdílený typ může být buď primitivní typ modulu runtime, nebo může zahrnovat vytvoření nového sdíleného typu ve sdíleném sestavení.  Sdílený typ je často [rozhraní](../../csharp/language-reference/keywords/interface.md) definované v sestavení aplikace. Viz také: [jak se sdílí závislosti?](#how-are-dependencies-shared).

2. Použijte techniky zařazování pro převod z jednoho typu na jiný.
