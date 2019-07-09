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
ms.openlocfilehash: 06dbc4b7124aa873fd8471794fa25b0f47f8ce3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663581"
---
# <a name="observer-design-pattern"></a>Návrhový vzor Pozorovatel

Návrhový vzor pozorovatel umožňuje předplatiteli zaregistrovat se a dostávat upozornění od poskytovatele. Je vhodný pro jakýkoli scénář, který vyžaduje nabízené oznámení. Definuje vzor *poskytovatele* (označované také jako *subjektu* nebo *pozorovat*) a nula, jeden nebo více *pozorovatelů*. Pozorovatelé zaregistrovat u poskytovatele a pokaždé, když předdefinovanou podmínku, události nebo změnu stavu dochází, zprostředkovatel automaticky upozorní všechny pozorovatelů ve volání jedné z jejich metod. Při volání této metody zprostředkovatele lze také poskytovat aktuální informace o stavu pozorovatelů. V rozhraní .NET Framework, se použije návrhový vzor pozorovatel implementací Obecné <xref:System.IObservable%601?displayProperty=nameWithType> a <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Parametr obecného typu představuje typ, který poskytuje informace o oznámení.

## <a name="applying-the-pattern"></a>Použití tohoto vzoru

Návrhový vzor pozorovatel je vhodná pro distribuované nabízené oznámení, protože umožňuje čisté oddělení mezi dva různé součásti nebo vrstvy aplikace, jako je například vrstva (obchodní logiky) zdroj dat a vrstvě uživatelského rozhraní (Zobrazit). Vzorek je možné implementovat pokaždé, když se poskytovatel používá zpětná volání k poskytování své klienty s aktuální informace.

Implementace vzoru vyžaduje, musíte poskytnout následující:

- Zprostředkovatel nebo předmětu, což je objekt, který odesílá oznámení pozorovatele. Zprostředkovatel je třída nebo struktura, která implementuje <xref:System.IObservable%601> rozhraní. Zprostředkovatel musí implementovat jedinou metodu <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, která je volána metodou pozorovatelé, které chcete dostávat upozornění od poskytovatele.

- Pozorovatele, který je objekt, který dostává oznámení ze zprostředkovatele. Pozorovatelem je třída nebo struktura, která implementuje <xref:System.IObserver%601> rozhraní. Pozorovatel musí implementovat tři metody, které se nazývají zprostředkovatelem:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, který poskytuje pozorovatel s informacemi o nových nebo aktuální.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, který informuje pozorovatele, který došlo k chybě.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, což znamená, že zprostředkovatel dokončení odesílání oznámení.

- Mechanismus, který umožňuje poskytovateli udržovat přehled o pozorovatelů. Obvykle, poskytovatel použije objekt kontejneru, jako <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objekt obsahovat odkazy na <xref:System.IObserver%601> implementace, které mají přihlásili k odběru oznámení. Použití kontejner úložiště pro tento účel umožňuje poskytovateli zpracování nula k neomezenému počtu pozorovatelů. Není definováno pořadí, ve kterém pozorovatelů dostávat oznámení; Zprostředkovatel je můžete použít libovolnou metodu pro určení pořadí.

- <xref:System.IDisposable> Implementace, která umožňuje poskytovateli odeberte pozorovatelů po oznámení dokončení. Pozorovatelé zobrazí odkaz na <xref:System.IDisposable> implementaci <xref:System.IObservable%601.Subscribe%2A> metoda, takže můžete také volat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda k odhlášení odběru před dokončením příkazu se zprostředkovatel, odesílání oznámení.

- Objekt, který obsahuje data, která odešle zprostředkovatel jeho pozorovatelů. Typ tohoto objektu, který odpovídá parametru obecného typu <xref:System.IObservable%601> a <xref:System.IObserver%601> rozhraní. I když tento objekt může být stejný jako <xref:System.IObservable%601> implementace, nejčastěji je samostatného typu.

> [!NOTE]
> Kromě provádění návrhový vzor pozorovatel vás může zajímat zkoumání knihovny, které se vytvářejí pomocí <xref:System.IObservable%601> a <xref:System.IObserver%601> rozhraní. Například [Reactive Extensions pro platformu .NET (obdx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) sestávat z několika metod rozšíření a pořadí standardní operátory LINQ, aby podporoval asynchronní programování.

## <a name="implementing-the-pattern"></a>Implementace vzoru

Návrhový vzor pozorovatel k implementaci informačním systému letiště sobě deklarace identity v následujícím příkladu. A `BaggageInfo` třída poskytuje informace o opravovány letů a karusel, kde je k dispozici pro vyzvednutí sobě z jednotlivých let. Je znázorněno v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

A `BaggageHandler` třídy zodpovídá za příjem informací o lety opravovány a sobě Karusel deklarací identity. Interně spravuje dvě kolekce:

- `observers` -Kolekce klienty, kteří budou dostávat aktualizované informace.

- `flights` -Kolekce letů a jejich přiřazené Karusel.

Obě kolekce jsou reprezentované pomocí obecného <xref:System.Collections.Generic.List%601> objekty, které jsou vytvořeny v `BaggageHandler` konstruktoru třídy. Zdrojový kód `BaggageHandler` třídy je znázorněno v následujícím příkladu.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienti, kteří si nepřejete dostávat aktualizované informace volání `BaggageHandler.Subscribe` metody. Pokud klient nebyl dříve přihlásili k odběru oznámení, odkaz na straně klienta <xref:System.IObserver%601> implementace je přidán do `observers` kolekce.

Přetížené `BaggageHandler.BaggageStatus` metodu lze volat pro označení, že sobě z let uvolňován, nebo je již uvolněna. V prvním případě metodě je předána číslo letu, letiště, ze kterého pochází letu a karuselu kde sobě uvolňován. V druhém případě metodě je předána jenom číslo letu. K sobě, která se zrušilo jeho načtení, metoda zkontroluje, jestli `BaggageInfo` informace předaný metodě existuje v `flights` kolekce. Pokud tomu tak není, metoda přidá informace a zavolá každý pozorovatel `OnNext` metody. Pro lety, jehož sobě již probíhá uvolnění, metoda zkontroluje, zda informace na této cestě jsou uloženy v `flights` kolekce. Pokud se jedná, volá metodu každý pozorovatel `OnNext` metoda a odebere `BaggageInfo` objektu z `flights` kolekce.

Při poslední letu dne má dostali a zpracovala jeho sobě `BaggageHandler.LastBaggageClaimed` metoda je volána. Tato metoda volá každý pozorovatel `OnCompleted` indikace, že všechna oznámení dokončení a poté vymaže `observers` kolekce.

Poskytovatele <xref:System.IObservable%601.Subscribe%2A> vrátí metoda <xref:System.IDisposable> implementace, která umožňuje pozorovatelů k ukončení přijímání oznámení před <xref:System.IObserver%601.OnCompleted%2A> metoda je volána. Zdrojový kód `Unsubscriber(Of BaggageInfo)` třídy je znázorněno v následujícím příkladu. Když je vytvořena instance třídy v `BaggageHandler.Subscribe` metodě je předána odkazem na `observers` kolekce a odkaz na pozorovatele, který je přidán do kolekce. Tyto odkazy jsou přiřazeny k místní proměnné. Při objektu `Dispose` metoda je volána, zkontroluje, zda pozorovatel stále existuje v `observers` kolekce a pokud ano, odebere pozorovatele.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Následující příklad uvádí <xref:System.IObserver%601> implementace s názvem `ArrivalsMonitor`, což je základní třída, která zobrazí informace o deklaraci identity sobě. Informace se zobrazí abecedně, podle názvu původní město. Metody `ArrivalsMonitor` jsou označeny jako `overridable` (v jazyce Visual Basic) nebo `virtual` (v C#), takže je lze všechny přepsat v odvozené třídě.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor` Třída zahrnuje `Subscribe` a `Unsubscribe` metody. `Subscribe` Metoda umožňuje třídě Uložit <xref:System.IDisposable> implementace vrácený voláním na <xref:System.IObservable%601.Subscribe%2A> privátní proměnné. `Unsubscribe` Metoda umožňuje třídě odběr oznámení voláním poskytovatele se <xref:System.IDisposable.Dispose%2A> implementace. `ArrivalsMonitor` také poskytuje implementace <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, a <xref:System.IObserver%601.OnCompleted%2A> metody. Pouze <xref:System.IObserver%601.OnNext%2A> značné množství kódu obsahuje implementaci. Metoda pracuje s privátní, seřazený, obecný <xref:System.Collections.Generic.List%601> objekt, který uchovává informace o letištích počátek opravovány letů a karusel, na kterých je jejich sobě k dispozici. Pokud `BaggageHandler` třídy hlásí nový doručení letu, <xref:System.IObserver%601.OnNext%2A> implementace metody přidá informace o této cestě do seznamu. Pokud `BaggageHandler` třídy hlásí, že letu sobě byl uvolněn, <xref:System.IObserver%601.OnNext%2A> metoda odstraní tento let ze seznamu. Pokaždé, když dojde ke změně, je v seznamu seřazené a zobrazí v konzole.

Následující příklad obsahuje vstupní bod aplikace, která vytváří instanci `BaggageHandler` třídy a také dvě instance `ArrivalsMonitor` třídy a používá `BaggageHandler.BaggageStatus` metodu pro přidání a odebrání informací o opravovány lety. V obou případech pozorovatelů získávat aktualizace a správně zobrazit informace o deklaraci identity sobě.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Popisuje osvědčené postupy při vývoji aplikací, které implementují návrhový vzor pozorovatel přijmout.|
|[Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)|Poskytuje podrobné implementaci zprostředkovatele pro teploty monitorování aplikace.|
|[Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)|Poskytuje podrobné provádění pozorovatele pro teploty monitorování aplikace.|
