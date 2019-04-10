---
title: 'Postupy: Implementace poskytovatele'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12c229b3a1436f9794258fec13905cce0fb767aa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324770"
---
# <a name="how-to-implement-a-provider"></a>Postupy: Implementace poskytovatele
Návrhový vzor pozorovatel vyžaduje rozdělení poskytovatele, který monitoruje dat a odešle oznámení, a jeden nebo více pozorovatelé, které obdrží oznámení (zpětná volání) od poskytovatele. Toto téma popisuje, jak vytvořit poskytovatele. Související téma [jak: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md), popisuje, jak vytvořit pozorovatele.  
  
### <a name="to-create-a-provider"></a>Chcete-li vytvořit poskytovatele  
  
1. Definování dat, která je odpovědná za zasílání pozorovatelů zprostředkovatele. I když se jeden typ může být zprostředkovatel a data, která se odešle do pozorovatelé, jsou obecně reprezentované pomocí různých typů. Například v teploty monitorování aplikace `Temperature` struktury definuje data, která zprostředkovatele (která je reprezentována `TemperatureMonitor` třídy definované v dalším kroku) monitoruje a do které pozorovatelů přihlášení k odběru.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Definování poskytovatele dat, což je typ, který implementuje <xref:System.IObservable%601?displayProperty=nameWithType> rozhraní. Argument obecného typu zprostředkovatele je typ, který odešle zprostředkovatel pozorovatelů. Následující příklad definuje `TemperatureMonitor` třídy, která je konstruovaný <xref:System.IObservable%601?displayProperty=nameWithType> implementace s argumentem obecného typu z `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Zjistěte, jak se zprostředkovatel ukládají odkazy na pozorovatelů tak, aby každý pozorovatel můžete být upozorněni v případě potřeby. Nejčastěji objekt kolekce například obecný <xref:System.Collections.Generic.List%601> objekt se používá pro tento účel. Následující příklad definuje privátní <xref:System.Collections.Generic.List%601> objekt, který je vytvořena instance v `TemperatureMonitor` konstruktoru třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Definování <xref:System.IDisposable> implementace, která vrací zprostředkovatele pro předplatitele tak, aby se můžete zastavit příjem oznámení v každém okamžiku. Následující příklad definuje vnořený `Unsubscriber` třídy, který je předán odkaz na kolekci odběratele a odběrateli, když je vytvořena instance třídy. Tento kód povoluje odběratele pro volání objektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace kolekce předplatitele.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implementace <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody. Metodě je předána odkazem na <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní a by měla být uložena v objektu pro tento účel v kroku 3. Metoda by měla pak se vraťte <xref:System.IDisposable> implementace vyvinuté v kroku 4. Následující příklad ukazuje implementaci <xref:System.IObservable%601.Subscribe%2A> metodu `TemperatureMonitor` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Oznámení pozorovatele podle potřeby voláním jejich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace. V některých případech se nemusí volat zprostředkovatele <xref:System.IObserver%601.OnError%2A> metodu, když dojde k chybě. Například následující `GetTemperature` metoda simuluje monitorování, která čte data o teplotě každých pět sekund a pozorovatelů upozorní, když teplota od předchozí čtení změněno v alespoň.1 úhlu. Pokud zařízení nehlásí teplota (to znamená, pokud její hodnota je null), zprostředkovatele oznámí pozorovatelé, přenos je dokončena. Všimněte si, že kromě volání každý pozorovatel <xref:System.IObserver%601.OnCompleted%2A> metody, `GetTemperature` metoda vymaže <xref:System.Collections.Generic.List%601> kolekce. V takovém případě poskytovateli díky žádná volání <xref:System.IObserver%601.OnError%2A> metoda jeho pozorovatelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní zdrojový kód pro definování <xref:System.IObservable%601> implementace teploty monitorování aplikace. Zahrnuje `Temperature` strukturu, která se data odeslaná do pozorovatelé, a `TemperatureMonitor` třídy, která je <xref:System.IObservable%601> implementace.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IObservable%601>
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
