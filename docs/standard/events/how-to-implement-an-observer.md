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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139312"
---
# <a name="how-to-implement-an-observer"></a>Postupy: Implementace pozorovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi pozorovatele, který registruje oznámení, a zprostředkovatelem, který sleduje data a odesílá oznámení jednomu nebo více pozorovatelům. Toto téma popisuje, jak vytvořit pozorovatele. Související [téma: Implementace zprostředkovatele](../../../docs/standard/events/how-to-implement-a-provider.md), popisuje, jak vytvořit zprostředkovatele.  
  
### <a name="to-create-an-observer"></a>Vytvoření pozorovatele  
  
1. Definujte pozorovatele, což je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Například následující kód definuje typ `TemperatureReporter` s názvem, <xref:System.IObserver%601?displayProperty=nameWithType> který je vyrobenou `Temperature`implementací s argumentem obecného typu .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Pokud pozorovatel může zastavit příjem oznámení před <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> zprostředkovatelvolá jeho provádění, definujte soukromou proměnnou, která bude obsahovat <xref:System.IDisposable> implementaci vrácenou metodou zprostředkovatele. <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> Měli byste také definovat metodu předplatného, <xref:System.IObservable%601.Subscribe%2A> která volá <xref:System.IDisposable> metodu zprostředkovatele a ukládá vrácený objekt. Například následující kód definuje privátní proměnnou `unsubscriber` s názvem a definuje metodu, `Subscribe` která volá <xref:System.IObservable%601.Subscribe%2A> metodu zprostředkovatele a přiřadí vrácený objekt `unsubscriber` proměnné.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Definujte metodu, která umožňuje pozorovateli zastavit příjem <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> oznámení před zprostředkovatelvolá jeho implementaci, pokud je tato funkce požadována. Následující příklad definuje `Unsubscribe` metodu.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Uveďte implementace tří metod <xref:System.IObserver%601> definovaných <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>rozhraním: , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. V závislosti na zprostředkovatele a potřebách aplikace <xref:System.IObserver%601.OnError%2A> a <xref:System.IObserver%601.OnCompleted%2A> metody mohou být zástupné procedury implementace. Všimněte <xref:System.IObserver%601.OnError%2A> si, že metoda <xref:System.Exception> by neměla zpracovávat předané objekt jako <xref:System.IObserver%601.OnCompleted%2A> <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> výjimku a metoda je zdarma volat implementaci zprostředkovatele. Následující příklad ukazuje <xref:System.IObserver%601> implementaci `TemperatureReporter` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje úplný zdrojový `TemperatureReporter` kód pro třídu, která poskytuje <xref:System.IObserver%601> implementaci pro aplikaci pro sledování teploty.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IObserver%601>
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
