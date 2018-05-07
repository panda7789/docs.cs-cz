---
title: Návrhový vzor Pozorovatel
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1dbd2c991f4b4259caa180375283ecb6d957336
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="observer-design-pattern"></a>Návrhový vzor Pozorovatel
Návrhový vzor pozorovatel umožňuje odběratele k registraci nebo dostávat oznámení od zprostředkovatele. Je vhodná pro každý scénář, který vyžaduje nabízená oznámení. Definuje vzoru *zprostředkovatele* (také označované jako *subjektu* nebo *lze zobrazit*) a nula, jednu nebo více *pozorovatelů*. Pozorovatelů zaregistrovat u zprostředkovatele a vždy, když předdefinovanou podmínku, události nebo změna stavu dojde, zprostředkovatel automaticky oznámí všechny pozorovatelů pomocí volání jeden své metody. Při volání této metody zprostředkovatele můžete také poskytnout aktuální informace o stavu pozorovatelů. V rozhraní .NET Framework, je použít návrhový vzor pozorovatel implementací obecná <xref:System.IObservable%601?displayProperty=nameWithType> a <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Parametr obecného typu představuje typ, který poskytuje informace o oznámení.  
  
## <a name="applying-the-pattern"></a>Použití vzoru  
 Návrhový vzor pozorovatel je vhodná pro distribuované nabízená oznámení, protože podporuje čistou oddělení mezi dva různé součásti nebo aplikačními vrstvami, jako je například vrstvu (obchodní logiku) zdroj dat a uživatelské rozhraní (zobrazení) vrstvě. Vzor se dá implementovat pokaždé, když poskytovatele zpětná volání použije k poskytování jeho klienty s aktuální informace.  
  
 Implementace vzoru vyžaduje zadání následující:  
  
-   Zprostředkovatele nebo předmětu, což je objekt, který odesílá oznámení pozorovatele. Zprostředkovatel je třídu nebo strukturu, která implementuje <xref:System.IObservable%601> rozhraní. Zprostředkovatel musí implementovat jednu metodu, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, která je volána metodou pozorovatelů, které chcete dostávat oznámení od zprostředkovatele.  
  
-   Pozorovatel, což je objekt, který obdrží oznámení ze zprostředkovatele. Pozorovatel je třídu nebo strukturu, která implementuje <xref:System.IObserver%601> rozhraní. Pozorovatel musí implementovat tři metody, které se nazývají zprostředkovatelem:  
  
    -   <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, který poskytuje pozorovatel s aktuální nebo nové informace.  
  
    -   <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, která informuje pozorovatel, který došlo k chybě.  
  
    -   <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, což naznačuje, že zprostředkovatel bylo dokončeno odesílání oznámení.  
  
-   Mechanismus, který umožňuje poskytovateli ke sledování pozorovatelů. Obvykle používá zprostředkovatel objekt kontejneru, například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objektu k udržení odkazů na <xref:System.IObserver%601> implementace, které odebírá oznámení. Použití kontejner úložiště pro tento účel umožňuje zprostředkovatele pro zpracování nula na neomezený počet pozorovatelů. Pořadí, ve kterém pozorovatelů obdrží oznámení není definován; Zprostředkovatel je můžete použít libovolnou metodu pro určení pořadí.  
  
-   <xref:System.IDisposable> Implementace, která umožňuje poskytovateli odeberte pozorovatelů po dokončení oznámení. Pozorovatelů zobrazí odkaz na <xref:System.IDisposable> implementace z <xref:System.IObservable%601.Subscribe%2A> metoda, takže můžete také zavolat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda k odhlášení odběru před zprostředkovatele dokončila odesílání oznámení.  
  
-   Objekt, který obsahuje data, která odešle zprostředkovatel jeho pozorovatelů. Typ tohoto objektu odpovídá parametr obecného typu <xref:System.IObservable%601> a <xref:System.IObserver%601> rozhraní. I když tento objekt může být stejný jako <xref:System.IObservable%601> implementace nejčastěji je samostatný typu.  
  
> [!NOTE]
>  Kromě implementace návrhový vzor pozorovatel, vás může zajímat zkoumat knihovny, které jsou vytvořené pomocí <xref:System.IObservable%601> a <xref:System.IObserver%601> rozhraní. Například [reaktivní rozšíření pro platformu .NET (Rx)](https://msdn.microsoft.com/library/hh242985.aspx) obsahují sadu metod rozšíření a operátory standardní pořadí LINQ pro podporu asynchronní programování.  
  
## <a name="implementing-the-pattern"></a>Implementace vzoru  
 Následující příklad používá návrhový vzor pozorovatel k implementaci informace systému letiště sobě deklarace identity. A `BaggageInfo` třída poskytuje informace o které letů a karusely, kde je k dispozici pro vyzvednutí sobě z každý let. Zobrazí se v následujícím příkladu.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
 [!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]  
  
 A `BaggageHandler` třída je odpovědná za přijímá informace, o které letů a sobě deklarací karusely. Interně udržuje dvě kolekce:  
  
-   `observers` -Kolekci klientů, kteří je budou přijímat aktualizované informace.  
  
-   `flights` -Kolekce letů a jejich přiřazené karusely.  
  
 Obě kolekce jsou reprezentované pomocí obecného <xref:System.Collections.Generic.List%601> objekty, které jsou vytvářeny instance v `BaggageHandler` konstruktoru třídy. Zdrojový kód `BaggageHandler` třída je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
 [!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]  
  
 Volání klientů, které chcete přijímat aktualizované informace `BaggageHandler.Subscribe` metoda. Pokud klient nebyl dříve přihlásit k odběru oznámení, odkaz na klienta <xref:System.IObserver%601> implementace je přidán do `observers` kolekce.  
  
 Přetížené `BaggageHandler.BaggageStatus` nelze volat metodu že sobě z letu odpojení, nebo už odpojení. V prvním případě metodu je předán číslo letu, ze kterého pochází letu letiště a karuselu kde sobě odpojení. V druhém případě je předán metodu jenom číslo letu. Pro sobě, který je odpojeno, metoda kontroly jestli `BaggageInfo` informace předaný metodě existuje v `flights` kolekce. Pokud ne, metoda přidá informace a volá každý pozorovatel `OnNext` metoda. Metoda pro lety, jejichž sobě už odpojení, zkontroluje, zda informace na této cestě jsou uloženy v `flights` kolekce. Pokud se jedná, volá metodu každý pozorovatel `OnNext` metoda a odebere `BaggageInfo` objektu z `flights` kolekce.  
  
 Když má dostali poslední letu dne a zpracovala jeho sobě `BaggageHandler.LastBaggageClaimed` metoda je volána. Tato metoda volá každý pozorovatel `OnCompleted` metoda indikující, že byly dokončeny všechny oznámení a pak zruší `observers` kolekce.  
  
 Poskytovatele <xref:System.IObservable%601.Subscribe%2A> metoda vrátí <xref:System.IDisposable> implementace, která umožňuje pozorovatelů zastavit přijímání oznámení před <xref:System.IObserver%601.OnCompleted%2A> metoda je volána. Zdrojový kód pro tuto `Unsubscriber(Of BaggageInfo)` třída je znázorněno v následujícím příkladu. Když je vytvořena instance třídy v `BaggageHandler.Subscribe` metoda, je předán odkaz na `observers` kolekce a odkaz na pozorovatel, který je přidán do kolekce. Tyto odkazy jsou přiřazeny k lokální proměnné. Když objektu `Dispose` metoda je volána, zkontroluje, zda stále existuje pozorovatel v `observers` kolekce a pokud ano, odebere pozorovatele.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
 [!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]  
  
 Následující příklad uvádí <xref:System.IObserver%601> implementace s názvem `ArrivalsMonitor`, což je základní třídu, která zobrazuje informace o sobě deklaraci identity. Název města, původní je abecedně, zobrazují informace. Metody `ArrivalsMonitor` jsou označeny jako `overridable` (v jazyce Visual Basic) nebo `virtual` (v jazyku C#), takže je můžete všechny přepsat odvozenou třídou.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
 [!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]  
  
 `ArrivalsMonitor` Třída zahrnuje `Subscribe` a `Unsubscribe` metody. `Subscribe` Metoda umožňuje třídě Uložit <xref:System.IDisposable> implementace vrácený volání <xref:System.IObservable%601.Subscribe%2A> soukromé proměnné. `Unsubscribe` Metoda umožňuje třídě zrušit odběr oznámení voláním poskytovatele <xref:System.IDisposable.Dispose%2A> implementace. `ArrivalsMonitor` také poskytuje implementace <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, a <xref:System.IObserver%601.OnCompleted%2A> metody. Pouze <xref:System.IObserver%601.OnNext%2A> implementace obsahuje významné množství kódu. Metoda funguje s privátní, seřazené, obecného <xref:System.Collections.Generic.List%601> objekt, který uchovává informace o letištích původu, pro které lety a karusely, na kterých je k dispozici jejich sobě. Pokud `BaggageHandler` třída sestavy nové příchodem letu, <xref:System.IObserver%601.OnNext%2A> implementace metod přidá do seznamu informace o této cestě. Pokud `BaggageHandler` třída hlásí, že letu na sobě byl odpojen, <xref:System.IObserver%601.OnNext%2A> metoda odebere ze seznamu tento let. Vždy, když dojde ke změně, seznam seřazen a zobrazení v konzole.  
  
 Následující příklad obsahuje vstupní bod aplikace, který vytvoří instanci `BaggageHandler` třídy a také dvě instance `ArrivalsMonitor` třídy a používá `BaggageHandler.BaggageStatus` metoda přidávat a odebírat informace o které lety. V každém případě pozorovatelů přijímat aktualizace a správně zobrazit informace o sobě deklaraci identity.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
 [!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Popisuje osvědčené postupy při vývoji aplikace, které implementují návrhový vzor pozorovatel přijmout.|  
|[Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)|Poskytuje podrobné implementaci zprostředkovatele pro teplotě monitorování aplikace.|  
|[Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)|Poskytuje podrobné implementace pozorovatele pro teplotě monitorování aplikace.|
