---
title: Návrhový vzor Pozorovatel
description: Seznamte se se vzorem návrhu pozorovatele v .NET. Tento model umožňuje předplatitelům registraci a přijímání oznámení od poskytovatele.
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
ms.openlocfilehash: 4edcd2645b28095f4bd18f4918b9afa5c893bd39
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662729"
---
# <a name="observer-design-pattern"></a>Návrhový vzor Pozorovatel

Návrhový vzor pozorovatele umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele. Je vhodný pro jakýkoli scénář, který vyžaduje oznámení na základě nabízených oznámení. Vzor definuje *poskytovatele* (označovaného také jako *Předmět* nebo *pozorovatelný*) a nula, jedno nebo více *pozorovatelů*. Pozorovatelé se registrují u poskytovatele a pokaždé, když dojde ke změně předdefinované podmínky, události nebo stavu, poskytovatel automaticky upozorní všechny pozorovatele tím, že zavolá jednu z jejich metod. V rámci tohoto volání metody může poskytovatel také poskytnout informace o aktuálním stavu pozorovatelům. V .NET Framework se vzor návrhu pozorovatele používá implementací obecného <xref:System.IObservable%601?displayProperty=nameWithType> <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní a. Parametr obecného typu představuje typ, který poskytuje informace o oznámení.

## <a name="applying-the-pattern"></a>Použití vzoru

Vzor návrhu pozorovatele je vhodný pro distribuované oznámení založené na nabízených oznámeních, protože podporuje čisté oddělení mezi dvěma různými komponentami nebo aplikačními vrstvami, jako je například vrstva zdroje dat (obchodní logika) a vrstva uživatelského rozhraní (zobrazení). Vzor lze implementovat vždy, když poskytovatel používá zpětná volání k dodávání svých klientů k aktuálním informacím.

Implementace vzoru vyžaduje, abyste zadali následující:

- Poskytovatel nebo předmět, což je objekt, který odesílá oznámení pozorovatelům. Zprostředkovatel je třída nebo struktura, která implementuje <xref:System.IObservable%601> rozhraní. Zprostředkovatel musí implementovat jedinou metodu, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> , která je volána pozorovateli, kteří chtějí dostávat oznámení od poskytovatele.

- Pozorovatel, což je objekt, který přijímá oznámení od poskytovatele. Pozorovatel je třída nebo struktura, která implementuje <xref:System.IObserver%601> rozhraní. Pozorovatel musí implementovat tři metody, které jsou volány zprostředkovatelem:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, který poskytuje pozorovatele nové nebo aktuální informace.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, který informuje pozorovatele, že došlo k chybě.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, což znamená, že poskytovatel dokončil odesílání oznámení.

- Mechanismus, který umožňuje poskytovateli sledovat pozorovatele. Poskytovatel obvykle používá objekt kontejneru, jako je například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt, k blokování odkazů na <xref:System.IObserver%601> implementace, které mají odběr oznámení. Použití kontejneru úložiště pro tento účel umožňuje poskytovateli, aby zpracovával nulu na neomezený počet pozorovatelů. Pořadí, ve kterém pozorovatelé obdrží oznámení, nejsou definovány. Poskytovatel je bezplatný pro určení pořadí pomocí libovolné metody.

- <xref:System.IDisposable>Implementace umožňující poskytovateli odebrat pozorovatele, když je oznámení dokončeno. Pozorovatelé obdrží odkaz na <xref:System.IDisposable> implementaci z <xref:System.IObservable%601.Subscribe%2A> metody, takže mohou také volat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodu pro zrušení odběru předtím, než poskytovatel dokončí odesílání oznámení.

- Objekt obsahující data, která poskytovatel pošle pozorovatelům. Typ tohoto objektu odpovídá obecnému parametru typu <xref:System.IObservable%601> <xref:System.IObserver%601> rozhraní a. I když tento objekt může být stejný jako <xref:System.IObservable%601> implementace, nejčastěji je to samostatný typ.

> [!NOTE]
> Kromě implementace návrhového vzoru pozorovatele může být zajímat, jak prozkoumat knihovny sestavené pomocí <xref:System.IObservable%601> <xref:System.IObserver%601> rozhraní a. Například [reaktivní rozšíření pro .NET (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) se skládají ze sady rozšiřujících metod a operátorů LINQ standard pro podporu asynchronního programování.

## <a name="implementing-the-pattern"></a>Implementace vzoru

V následujícím příkladu je použit vzor návrhu pozorovatele k implementaci systému informací o deklaraci zavazadel na letišti. `BaggageInfo`Třída poskytuje informace o přicházejících letů a karuselech, kde je možné vyzvednutí zavazadel z každého letu. Zobrazuje se v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

`BaggageHandler`Třída zodpovídá za příjem informací o přicházejících v letech a karuselech nároků na zavazadla. Interně udržuje dvě kolekce:

- `observers`– Kolekce klientů, kteří získají aktualizované informace.

- `flights`– Kolekce letů a jejich přiřazené karusely.

Obě kolekce jsou reprezentovány obecnými <xref:System.Collections.Generic.List%601> objekty, které jsou vytvořeny v `BaggageHandler` konstruktoru třídy. Zdrojový kód `BaggageHandler` třídy je zobrazen v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienti, kteří chtějí získávat aktualizované informace, volají `BaggageHandler.Subscribe` metodu. Pokud se klient předtím, než se přihlásí k odběru oznámení, <xref:System.IObserver%601> přidá do kolekce odkaz na implementaci klienta `observers` .

`BaggageHandler.BaggageStatus`Metodu přetížení lze volat k označení toho, že se zavazadlo z letu buď nenačítá, nebo se už neuvolní. V prvním případě se metodě předává letová čísla, letiště, ze kterého let pochází, a karusel, v němž je zavazadlo uvolněno. Ve druhém případě je metoda předána pouze letovému číslu. U zavazadla, která je uvolněna, metoda zkontroluje, zda `BaggageInfo` informace předané metodě existují v `flights` kolekci. Pokud tomu tak není, metoda přidá informace a zavolá metodu pozorovatele `OnNext` . Pro lety, jejichž zavazadlo se už nenačítá, metoda zkontroluje, jestli jsou informace o tomto letu uložené v `flights` kolekci. Pokud je, metoda volá každou metodu pozorovatele `OnNext` a odebere `BaggageInfo` objekt z `flights` kolekce.

Po vykládce posledního letu dne a jeho zavazadla byla `BaggageHandler.LastBaggageClaimed` metoda volána. Tato metoda volá každou metodu pozorovatele, `OnCompleted` aby označovala, že všechna oznámení byla dokončena, a poté vymaže `observers` kolekci.

<xref:System.IObservable%601.Subscribe%2A>Metoda poskytovatele vrátí <xref:System.IDisposable> implementaci, která umožňuje pozorovatelům zastavit příjem oznámení před <xref:System.IObserver%601.OnCompleted%2A> zavoláním metody. Zdrojový kód této `Unsubscriber(Of BaggageInfo)` třídy je zobrazen v následujícím příkladu. Když je v metodě vytvořena instance třídy `BaggageHandler.Subscribe` , je předána odkaz na `observers` kolekci a odkaz na pozorovatele, který je přidán do kolekce. Tyto odkazy jsou přiřazeny k místním proměnným. Když `Dispose` je volána metoda objektu, kontroluje, zda pozorovatel stále existuje v `observers` kolekci, a pokud ano, odebere pozorovatele.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Následující příklad poskytuje <xref:System.IObserver%601> implementaci s názvem `ArrivalsMonitor` , která je základní třídou, která zobrazuje informace o deklaraci zavazadel. Informace se zobrazují abecedně podle názvu původního města. Metody pro `ArrivalsMonitor` jsou označeny jako `overridable` (v Visual Basic) nebo `virtual` (v jazyce C#), takže je lze přepsat odvozenou třídou.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor`Třída obsahuje `Subscribe` `Unsubscribe` metody a. `Subscribe`Metoda umožňuje třídě Uložit <xref:System.IDisposable> implementaci vrácenou voláním do <xref:System.IObservable%601.Subscribe%2A> soukromé proměnné. `Unsubscribe`Metoda umožňuje třídě odhlásit odběr oznámení voláním <xref:System.IDisposable.Dispose%2A> implementace poskytovatele. `ArrivalsMonitor`poskytuje také implementace <xref:System.IObserver%601.OnNext%2A> <xref:System.IObserver%601.OnError%2A> metod, a <xref:System.IObserver%601.OnCompleted%2A> . Pouze <xref:System.IObserver%601.OnNext%2A> implementace obsahuje značný objem kódu. Metoda spolupracuje s privátním a seřazeným obecným <xref:System.Collections.Generic.List%601> objektem, který uchovává informace o letištích původu pro přicházející lety a karusely, na kterých je jejich zavazadlo k dispozici. Pokud `BaggageHandler` Třída ohlásí nové doručení letu, <xref:System.IObserver%601.OnNext%2A> implementace metody přidá do seznamu informace o tomto letu. Pokud `BaggageHandler` Třída hlásí, že je zavazadlo letu uvolněno, <xref:System.IObserver%601.OnNext%2A> Metoda z tohoto seznamu odstraní tento let. Pokaždé, když je provedena změna, seznam se seřadí a zobrazí v konzole.

Následující příklad obsahuje vstupní bod aplikace, který vytváří instanci `BaggageHandler` třídy, a také dvě instance `ArrivalsMonitor` třídy a používá `BaggageHandler.BaggageStatus` metodu k přidání a odebrání informací o přicházejících letů. V každém případě pozorovatelé obdrží aktualizace a správně zobrazují informace o nárokech na zavazadlo.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Doporučené postupy pro návrhový vzor Pozorovatel](observer-design-pattern-best-practices.md)|Popisuje osvědčené postupy, které je potřeba provést při vývoji aplikací, které implementují vzor návrhu pozorovatele.|
|[Postupy: implementace poskytovatele](how-to-implement-a-provider.md)|Poskytuje podrobnou implementaci zprostředkovatele pro aplikaci pro monitorování teploty.|
|[Postupy: implementace pozorovatele](how-to-implement-an-observer.md)|Poskytuje podrobnou implementaci pozorovatele pro aplikaci pro monitorování teploty.|
