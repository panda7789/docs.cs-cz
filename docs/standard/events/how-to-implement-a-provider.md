---
title: 'Postupy: Implementace poskytovatele'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0f99a611de4bc344a0fd35130a59d496126e3af5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-provider"></a>Postupy: Implementace poskytovatele
Návrhový vzor pozorovatel vyžaduje rozdělení zprostředkovatele, který monitoruje data a odešle oznámení, a jeden nebo více pozorovatelů, které dostávat oznámení (zpětná volání) od zprostředkovatele. Toto téma popisuje postup vytvoření poskytovatele. Související téma, [postupy: implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md), popisuje, jak vytvořit pozorovatele.  
  
### <a name="to-create-a-provider"></a>Chcete-li vytvořit poskytovatele  
  
1.  Zadejte data, která je odpovědná za zasílání pozorovatelů zprostředkovatele. I když mezi poskytovatelem a data, která odešle pozorovatelů může být jeden typ, jsou obecně reprezentované pomocí různých typů. Například v teplotě monitorování aplikace `Temperature` struktura definují data, která zprostředkovatele (která je reprezentována `TemperatureMonitor` třídy definované v dalším kroku) monitoruje a do které pozorovatelů přihlášení k odběru.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Zadejte poskytovatele dat, který je typ, který implementuje <xref:System.IObservable%601?displayProperty=nameWithType> rozhraní. Argument obecného typu poskytovatele je typ, který odešle zprostředkovatel pozorovatelů. V následujícím příkladu definuje `TemperatureMonitor` třída, která je vytvořený <xref:System.IObservable%601?displayProperty=nameWithType> implementace s argumentem obecného typu ve `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Zjistěte, jak se zprostředkovatel uloží odkazy na pozorovatelů tak, aby každý pozorovatel může být upozorněni, když je to vhodné. Nejčastěji objekt kolekce například obecný <xref:System.Collections.Generic.List%601> objekt se používá pro tento účel. V následujícím příkladu definuje privátního <xref:System.Collections.Generic.List%601> objekt, který je v instanci `TemperatureMonitor` konstruktoru třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Definování <xref:System.IDisposable> implementace, která může poskytovatel tak, aby se může zastavit příjem oznámení kdykoli vrátit odběratelům. V následujícím příkladu definuje vnořený `Unsubscriber` třídu, která byla předána odkaz na kolekci odběratele a k odběrateli, při vytváření instance třídy. Tento kód umožňuje odběratele pro volání objektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace do kolekce odběratele.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Implementace <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda. Metodě se předává odkaz na <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní a by měly být uložené v objektu určený pro tento účel v kroku 3. Metoda by měla pak se vraťte <xref:System.IDisposable> implementace vyvinuté v kroku 4. Následující příklad ukazuje implementaci <xref:System.IObservable%601.Subscribe%2A> metoda v `TemperatureMonitor` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Oznámit pozorovatelů podle potřeby voláním jejich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace. V některých případech nemusí volání zprostředkovatele <xref:System.IObserver%601.OnError%2A> metoda, když dojde k chybě. Například následující `GetTemperature` metoda simuluje monitorování, který čte data teploty každých pět sekund a pozorovatelů upozorní, pokud teplota došlo ke změně v alespoň.1 úhlu od předchozí čtení. Pokud zařízení nevytváří sestavu teplotě (to znamená, pokud je jeho hodnota null), zprostředkovatele oznámí pozorovatelů, přenos je dokončena. Všimněte si, že, kromě volání každý pozorovatel <xref:System.IObserver%601.OnCompleted%2A> metody `GetTemperature` metoda vymaže <xref:System.Collections.Generic.List%601> kolekce. V takovém případě zprostředkovatele provádí žádné volání na <xref:System.IObserver%601.OnError%2A> metoda jeho pozorovatelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní zdrojový kód pro definování <xref:System.IObservable%601> implementace teplotě monitorování aplikace. Obsahuje `Temperature` struktura, což je dat odesílaných pozorovatelů, a `TemperatureMonitor` třída, která je <xref:System.IObservable%601> implementace.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IObservable%601>  
 [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)  
 [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
