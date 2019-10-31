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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131578"
---
# <a name="observer-design-pattern"></a>Návrhový vzor Pozorovatel

Návrhový vzor pozorovatele umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele. Je vhodný pro jakýkoli scénář, který vyžaduje oznámení na základě nabízených oznámení. Vzor definuje *poskytovatele* (označovaného také jako *Předmět* nebo *pozorovatelný*) a nula, jedno nebo více *pozorovatelů*. Pozorovatelé se registrují u poskytovatele a pokaždé, když dojde ke změně předdefinované podmínky, události nebo stavu, poskytovatel automaticky upozorní všechny pozorovatele tím, že zavolá jednu z jejich metod. V rámci tohoto volání metody může poskytovatel také poskytnout informace o aktuálním stavu pozorovatelům. V .NET Framework se vzor návrhu pozorovatele používá implementací obecných rozhraní <xref:System.IObservable%601?displayProperty=nameWithType> a <xref:System.IObserver%601?displayProperty=nameWithType>. Parametr obecného typu představuje typ, který poskytuje informace o oznámení.

## <a name="applying-the-pattern"></a>Použití vzoru

Vzor návrhu pozorovatele je vhodný pro distribuované oznámení založené na nabízených oznámeních, protože podporuje čisté oddělení mezi dvěma různými komponentami nebo aplikačními vrstvami, jako je například vrstva zdroje dat (obchodní logika) a vrstva uživatelského rozhraní (zobrazení). Vzor lze implementovat vždy, když poskytovatel používá zpětná volání k dodávání svých klientů k aktuálním informacím.

Implementace vzoru vyžaduje, abyste zadali následující:

- Poskytovatel nebo předmět, což je objekt, který odesílá oznámení pozorovatelům. Zprostředkovatel je třída nebo struktura, která implementuje rozhraní <xref:System.IObservable%601>. Poskytovatel musí implementovat jedinou metodu, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, která je volána pozorovateli, kteří chtějí dostávat oznámení od poskytovatele.

- Pozorovatel, což je objekt, který přijímá oznámení od poskytovatele. Pozorovatel je třída nebo struktura, která implementuje rozhraní <xref:System.IObserver%601>. Pozorovatel musí implementovat tři metody, které jsou volány zprostředkovatelem:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, která pozorovatele dodá nové nebo aktuální informace.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, který informuje pozorovatele, že došlo k chybě.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, což znamená, že poskytovatel dokončil odesílání oznámení.

- Mechanismus, který umožňuje poskytovateli sledovat pozorovatele. Poskytovatel obvykle používá objekt kontejneru, jako je <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt, pro blokování odkazů na <xref:System.IObserver%601> implementace, které mají oznámení odebírané. Použití kontejneru úložiště pro tento účel umožňuje poskytovateli, aby zpracovával nulu na neomezený počet pozorovatelů. Pořadí, ve kterém pozorovatelé obdrží oznámení, nejsou definovány. Poskytovatel je bezplatný pro určení pořadí pomocí libovolné metody.

- <xref:System.IDisposable> implementace, která umožňuje poskytovateli odebrat pozorovatele, když je oznámení dokončeno. Pozorovatelé obdrží odkaz na <xref:System.IDisposable> implementaci z metody <xref:System.IObservable%601.Subscribe%2A>, takže mohou také volat metodu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> k odhlášení odběru předtím, než poskytovatel dokončí odesílání oznámení.

- Objekt obsahující data, která poskytovatel pošle pozorovatelům. Typ tohoto objektu odpovídá parametru obecného typu <xref:System.IObservable%601> a <xref:System.IObserver%601> rozhraní. I když tento objekt může být stejný jako implementace <xref:System.IObservable%601>, nejčastěji se jedná o samostatný typ.

> [!NOTE]
> Kromě implementace návrhového vzoru pozorovatele může být zajímání knihoven, které jsou sestaveny pomocí rozhraní <xref:System.IObservable%601> a <xref:System.IObserver%601>. Například [reaktivní rozšíření pro .NET (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) se skládají ze sady rozšiřujících metod a operátorů LINQ standard pro podporu asynchronního programování.

## <a name="implementing-the-pattern"></a>Implementace vzoru

V následujícím příkladu je použit vzor návrhu pozorovatele k implementaci systému informací o deklaraci zavazadel na letišti. `BaggageInfo` Třída poskytuje informace o přicházejících letů a karuselech, kde je možné vyzvednutí zavazadel z každého letu. Zobrazuje se v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

`BaggageHandler` třída zodpovídá za příjem informací o přicházejících v letech a karuselech nároků na zavazadla. Interně udržuje dvě kolekce:

- `observers` – kolekce klientů, kteří získají aktualizované informace.

- `flights` – kolekce letů a jejich přiřazené karusely.

Obě kolekce jsou reprezentovány obecnými <xref:System.Collections.Generic.List%601> objekty, které jsou vytvořeny v konstruktoru `BaggageHandler` třídy. V následujícím příkladu je uveden zdrojový kód pro třídu `BaggageHandler`.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienti, kteří chtějí získávat aktualizované informace, volají metodu `BaggageHandler.Subscribe`. Pokud se klient předtím, než se přihlásí k odběru oznámení, přidá do kolekce `observers` odkaz na implementaci <xref:System.IObserver%601> klienta.

Přetíženou metodu `BaggageHandler.BaggageStatus` lze volat k označení toho, že se zavazadlo z letu buď nenačítá, nebo se už neuvolní. V prvním případě se metodě předává letová čísla, letiště, ze kterého let pochází, a karusel, v němž je zavazadlo uvolněno. Ve druhém případě je metoda předána pouze letovému číslu. V případě, že dojde k uvolnění zavazadla, metoda ověří, zda `BaggageInfo` informace předané metodě existují v kolekci `flights`. Pokud tomu tak není, metoda přidá tyto informace a zavolá metodu `OnNext` pro každého pozorovatele. Pro lety, jejichž zavazadlo se už nenačítá, metoda zkontroluje, jestli jsou informace o tomto letu uložené v kolekci `flights`. Pokud je, volá metoda každou `OnNext` metodu pozorovatele a odebere objekt `BaggageInfo` z kolekce `flights`.

Po vykládce posledního letu dne a jeho zavazadla byla zavolána metoda `BaggageHandler.LastBaggageClaimed`. Tato metoda volá `OnCompleted` metodu každého pozorovatele, aby označovala, že všechna oznámení byla dokončena, a poté vymaže kolekci `observers`.

Metoda <xref:System.IObservable%601.Subscribe%2A> poskytovatele vrací implementaci <xref:System.IDisposable>, která umožňuje pozorovatelům zastavit příjem oznámení před zavoláním metody <xref:System.IObserver%601.OnCompleted%2A>. V následujícím příkladu je uveden zdrojový kód pro tuto třídu `Unsubscriber(Of BaggageInfo)`. Když je vytvořena instance třídy v metodě `BaggageHandler.Subscribe`, je předána odkaz na kolekci `observers` a odkaz na pozorovatele, který je přidán do kolekce. Tyto odkazy jsou přiřazeny k místním proměnným. Když je volána metoda `Dispose` objektu, zkontroluje, zda pozorovatel stále existuje v kolekci `observers` a pokud ano, odebere pozorovatele.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Následující příklad poskytuje <xref:System.IObserver%601> implementaci s názvem `ArrivalsMonitor`, která je základní třídou, která zobrazuje informace o deklaraci zavazadel. Informace se zobrazují abecedně podle názvu původního města. Metody `ArrivalsMonitor` jsou označeny jako `overridable` (v Visual Basic) nebo `virtual` (in C#), takže je lze přepsat odvozenou třídou.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

Třída `ArrivalsMonitor` obsahuje metody `Subscribe` a `Unsubscribe`. Metoda `Subscribe` umožňuje třídě ukládat implementaci <xref:System.IDisposable>, která byla vrácena voláním do <xref:System.IObservable%601.Subscribe%2A> privátní proměnné. Metoda `Unsubscribe` umožňuje třídě odhlásit odběr oznámení voláním implementace <xref:System.IDisposable.Dispose%2A> zprostředkovatele. `ArrivalsMonitor` také poskytuje implementace metod <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>a <xref:System.IObserver%601.OnCompleted%2A>. Pouze implementace <xref:System.IObserver%601.OnNext%2A> obsahuje značný objem kódu. Metoda spolupracuje s privátním, řazeným a obecným objektem <xref:System.Collections.Generic.List%601>, který uchovává informace o letištích původu pro přicházející lety a karusely, na kterých je jejich zavazadlo k dispozici. Pokud `BaggageHandler` třída hlásí nové doručení letu, implementace metody <xref:System.IObserver%601.OnNext%2A> přidá do seznamu informace o tomto letu. Pokud `BaggageHandler` třída hlásí, že se odstranilo zavazadlo letu, metoda <xref:System.IObserver%601.OnNext%2A> odstraní daný let ze seznamu. Pokaždé, když je provedena změna, seznam se seřadí a zobrazí v konzole.

Následující příklad obsahuje vstupní bod aplikace, který vytváří instanci `BaggageHandler` třídy, a také dvě instance třídy `ArrivalsMonitor` a používá metodu `BaggageHandler.BaggageStatus` k přidání a odebrání informací o přicházejících letů. V každém případě pozorovatelé obdrží aktualizace a správně zobrazují informace o nárokech na zavazadlo.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Popisuje osvědčené postupy, které je potřeba provést při vývoji aplikací, které implementují vzor návrhu pozorovatele.|
|[Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)|Poskytuje podrobnou implementaci zprostředkovatele pro aplikaci pro monitorování teploty.|
|[Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)|Poskytuje podrobnou implementaci pozorovatele pro aplikaci pro monitorování teploty.|
