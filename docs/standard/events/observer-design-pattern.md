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
ms.openlocfilehash: 817337cec604a431f9f7d4eacb04378ee0d3c227
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131578"
---
# <a name="observer-design-pattern"></a>Návrhový vzor Pozorovatel

Vzor návrhu pozorovatele umožňuje odběratele zaregistrovat a přijímat oznámení od zprostředkovatele. Je vhodný pro všechny scénáře, které vyžadují oznámení na základě nabízených oznámení. Vzor definuje *zprostředkovatele* (označované také jako *předmět* nebo *pozorovatelné)* a nula, jeden nebo více *pozorovatelů*. Pozorovatelé zaregistrovat u zprostředkovatele a vždy, když dojde k předdefinované podmínky, události nebo změny stavu, zprostředkovatel automaticky upozorní všechny pozorovatele voláním jedné z jejich metod. V této metodě volání zprostředkovatele můžete také poskytnout aktuální informace o stavu pozorovatelů. V rozhraní .NET Framework je návrhový vzor pozorovatele použit implementací obecného <xref:System.IObservable%601?displayProperty=nameWithType> a <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Obecný parametr typu představuje typ, který poskytuje informace o oznámení.

## <a name="applying-the-pattern"></a>Použití vzoru

Návrhový vzor pozorovatele je vhodný pro distribuovaná nabízená oznámení, protože podporuje čisté oddělení mezi dvěma různými součástmi nebo aplikačními vrstvami, jako je vrstva zdroje dat (obchodní logika) a vrstva uživatelského rozhraní (zobrazení). Vzor lze implementovat vždy, když zprostředkovatel používá zpětná volání k poskytování aktuálníinformace svým klientům.

Implementace vzoru vyžaduje, abyste zadali následující:

- Zprostředkovatel nebo předmět, což je objekt, který odesílá oznámení pozorovatelům. Zprostředkovatel je třída nebo struktura, <xref:System.IObservable%601> která implementuje rozhraní. Zprostředkovatel musí implementovat jednu metodu , <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>která je volána pozorovateli, kteří chtějí přijímat oznámení od zprostředkovatele.

- Pozorovatel, což je objekt, který přijímá oznámení od zprostředkovatele. Pozorovatel je třída nebo struktura, <xref:System.IObserver%601> která implementuje rozhraní. Pozorovatel musí implementovat tři metody, z nichž všechny jsou volány zprostředkovatelem:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, který pozorovateli poskytuje nové nebo aktuální informace.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, který informuje pozorovatele, že došlo k chybě.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, což znamená, že poskytovatel dokončil odesílání oznámení.

- Mechanismus, který umožňuje zprostředkovateli sledovat pozorovatele. Zprostředkovatel obvykle používá objekt kontejneru, jako <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> je například objekt, <xref:System.IObserver%601> k uložení odkazů na implementace, které se přihlásily k odběru oznámení. Použití kontejneru úložiště pro tento účel umožňuje zprostředkovateli zpracovat nulu na neomezený počet pozorovatelů. Pořadí, ve kterém pozorovatelé přijímají oznámení, není definováno; poskytovatel může k určení objednávky použít libovolnou metodu.

- Implementace, <xref:System.IDisposable> která umožňuje zprostředkovateli odebrat pozorovatele po dokončení oznámení. Pozorovatelé obdrží odkaz <xref:System.IDisposable> na <xref:System.IObservable%601.Subscribe%2A> implementaci z metody, takže <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> mohou také volat metodu odhlásit před poskytovatel dokončil odesílání oznámení.

- Objekt, který obsahuje data, která zprostředkovatel odešle svým pozorovatelům. Typ tohoto objektu odpovídá parametru obecného <xref:System.IObservable%601> <xref:System.IObserver%601> typu rozhraní a. Přestože tento objekt může <xref:System.IObservable%601> být stejný jako implementace, nejčastěji se jedná o samostatný typ.

> [!NOTE]
> Kromě implementace vzoru návrhu pozorovatele může být zájem o zkoumání knihoven, které jsou vytvořeny pomocí rozhraní <xref:System.IObservable%601> a. <xref:System.IObserver%601> Například [reaktivní rozšíření pro .NET (Rx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) se skládají ze sady metod rozšíření a operátorů standardní sekvence LINQ pro podporu asynchronního programování.

## <a name="implementing-the-pattern"></a>Implementace vzoru

Následující příklad používá vzor návrhu pozorovatele k implementaci informačního systému letištních zavazadel. Třída `BaggageInfo` poskytuje informace o příletech a kolotočech, kde jsou k dispozici zavazadla z každého letu k vyzvednutí. To je znázorněno v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Třída `BaggageHandler` je zodpovědná za příjem informací o příletech a karoucích s reklamací zavazadel. Interně udržuje dvě kolekce:

- `observers`- Kolekce klientů, kteří obdrží aktualizované informace.

- `flights`- Sbírka letů a jejich přidělené kolotoče.

Obě kolekce jsou reprezentovány obecné <xref:System.Collections.Generic.List%601> objekty, které `BaggageHandler` jsou vytvořeny v konstruktoru třídy. Zdrojový kód pro `BaggageHandler` třídu je uveden v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienti, kteří chtějí přijímat `BaggageHandler.Subscribe` aktualizované informace, volají metodu. Pokud klient dosud k odběru oznámení, odkaz na implementaci <xref:System.IObserver%601> klienta je `observers` přidán do kolekce.

Přetížená `BaggageHandler.BaggageStatus` metoda může být volána k označení, že zavazadla z letu je buď vykládána, nebo již není vykládána. V prvním případě je metoda předána číslo letu, letiště, ze kterého let vznikl, a kolotoč, kde je zavazadlo vykládáno. V druhém případě je metoda předána pouze číslo letu. U zavazadel, která jsou vykládána, `BaggageInfo` metoda zkontroluje, zda informace `flights` předané metodě existují ve sběru. Pokud tomu tak není, metoda přidá informace a `OnNext` volá metodu každého pozorovatele. U letů, jejichž zavazadla již nejsou vykládána, metoda kontroluje, `flights` zda jsou informace o tomto letu uloženy ve sbírce. Pokud je, metoda volá `OnNext` metodu každého pozorovatele `BaggageInfo` a `flights` odebere objekt z kolekce.

Po přistání posledního letu dne a zpracování jeho zavazadel `BaggageHandler.LastBaggageClaimed` se nazývá metoda. Tato metoda volá metody `OnCompleted` každého pozorovatele k označení, že všechna `observers` oznámení byla dokončena a potom vymaže kolekce.

Metoda zprostředkovatele <xref:System.IObservable%601.Subscribe%2A> vrátí <xref:System.IDisposable> implementaci, která umožňuje pozorovatelům zastavit <xref:System.IObserver%601.OnCompleted%2A> příjem oznámení před voláním metody. Zdrojový kód pro `Unsubscriber(Of BaggageInfo)` tuto třídu je uveden v následujícím příkladu. Při vytvoření instance třídy v `BaggageHandler.Subscribe` metodě, je předán `observers` odkaz na kolekci a odkaz na pozorovatele, který je přidán do kolekce. Tyto odkazy jsou přiřazeny k místním proměnným. Při `Dispose` volání metody objektu zkontroluje, zda pozorovatel stále `observers` existuje v kolekci a pokud ano, odebere pozorovatele.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Následující příklad obsahuje <xref:System.IObserver%601> implementaci `ArrivalsMonitor`s názvem , což je základní třída, která zobrazuje informace o nároku na zavazadla. Informace jsou zobrazeny abecedně podle názvu původního města. Metody jsou `ArrivalsMonitor` označeny `overridable` jako (v `virtual` jazyce Visual Basic) nebo (v jazyce C#), takže všechny mohou být přepsány odvozenou třídou.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

Třída `ArrivalsMonitor` obsahuje `Subscribe` metody `Unsubscribe` a. Metoda `Subscribe` umožňuje třídě uložit <xref:System.IDisposable> implementaci vrácenou voláním do <xref:System.IObservable%601.Subscribe%2A> soukromé proměnné. Metoda `Unsubscribe` umožňuje třídě odhlásit z oznámení voláním implementace <xref:System.IDisposable.Dispose%2A> zprostředkovatele. `ArrivalsMonitor`poskytuje také implementace <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>a <xref:System.IObserver%601.OnCompleted%2A> metody. Pouze <xref:System.IObserver%601.OnNext%2A> implementace obsahuje významné množství kódu. Metoda pracuje se soukromým, tříděným <xref:System.Collections.Generic.List%601> obecným objektem, který uchovává informace o letištích původu pro přílety a kolotoče, na kterých jsou k dispozici jejich zavazadla. Pokud `BaggageHandler` třída hlásí nový přílet, implementace <xref:System.IObserver%601.OnNext%2A> metody přidá informace o tomto letu do seznamu. Pokud `BaggageHandler` třída oznámí, že zavazadlo letu bylo <xref:System.IObserver%601.OnNext%2A> vyloženo, metoda tento let ze seznamu odstraní. Při každé změně je seznam seřazen a zobrazen v konzole.

Následující příklad obsahuje vstupní bod aplikace, který `BaggageHandler` inkonzisuje `ArrivalsMonitor` třídu a `BaggageHandler.BaggageStatus` dvě instance třídy a používá metodu k přidání a odebrání informací o příletových letech. V každém případě pozorovatelé obdrží aktualizace a správně zobrazí informace o reklamaci zavazadel.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Popisuje osvědčené postupy, které je třeba přijmout při vývoji aplikací, které implementují vzor návrhu pozorovatele.|
|[Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)|Poskytuje krok za krokem implementaci zprostředkovatele pro aplikaci pro sledování teploty.|
|[Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)|Poskytuje krok za krokem implementaci pozorovatele pro aplikaci sledování teploty.|
