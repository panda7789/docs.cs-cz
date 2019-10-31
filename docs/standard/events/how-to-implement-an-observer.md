---
title: 'Postupy: Implementace pozorovatele'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: e6aba4d85e502563291478640927bd0f234736a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139312"
---
# <a name="how-to-implement-an-observer"></a>Postupy: Implementace pozorovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi pozorovatelem, který registruje oznámení, a poskytovatelem, který monitoruje data a odesílá oznámení jednomu nebo více pozorovatelům. Toto téma popisuje, jak vytvořit pozorovatele. Související téma, [Postupy: implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md), popisuje, jak vytvořit poskytovatele.  
  
### <a name="to-create-an-observer"></a>Vytvoření pozorovatele  
  
1. Definujte pozorovatele, což je typ, který implementuje rozhraní <xref:System.IObserver%601?displayProperty=nameWithType>. Například následující kód definuje typ s názvem `TemperatureReporter`, který je vytvořená <xref:System.IObserver%601?displayProperty=nameWithType> implementace s argumentem obecného typu `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Pokud pozorovatel může zastavit příjem oznámení předtím, než poskytovatel zavolá jeho implementaci <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, definujte privátní proměnnou, která bude obsahovat implementaci <xref:System.IDisposable> vrácenou metodou <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> poskytovatele. Měli byste také definovat metodu předplatného, která volá metodu <xref:System.IObservable%601.Subscribe%2A> poskytovatele a uloží vrácený objekt <xref:System.IDisposable>. Například následující kód definuje soukromou proměnnou s názvem `unsubscriber` a definuje metodu `Subscribe`, která volá <xref:System.IObservable%601.Subscribe%2A> metodu poskytovatele a přiřadí vrácený objekt k `unsubscriber` proměnné.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Definujte metodu, která pozorovateli umožní zastavit příjem oznámení předtím, než poskytovatel zavolá implementaci <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, pokud je tato funkce povinná. Následující příklad definuje metodu `Unsubscribe`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Poskytněte implementace tří metod definovaných rozhraním <xref:System.IObserver%601>: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. V závislosti na poskytovateli a potřebách aplikace mohou být metody <xref:System.IObserver%601.OnError%2A> a <xref:System.IObserver%601.OnCompleted%2A> zástupné implementace. Všimněte si, že metoda <xref:System.IObserver%601.OnError%2A> by neměla zpracovávat předaný objekt <xref:System.Exception> jako výjimku a metoda <xref:System.IObserver%601.OnCompleted%2A> je bezplatná pro volání implementace <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> zprostředkovatele. Následující příklad ukazuje <xref:System.IObserver%601> implementaci `TemperatureReporter` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje úplný zdrojový kód pro třídu `TemperatureReporter`, která poskytuje implementaci <xref:System.IObserver%601> pro aplikaci monitorování teploty.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IObserver%601>
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
