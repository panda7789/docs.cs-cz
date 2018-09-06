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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6426e8bd138d06d3655562de6384e46a12c09279
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038650"
---
# <a name="how-to-implement-an-observer"></a>Postupy: Implementace pozorovatele
Návrhový vzor pozorovatel vyžaduje rozdělení pozorovatele, který registruje upozornění a poskytovatele, který monitoruje dat a odesílání oznámení na jeden nebo více pozorovatelů. Toto téma popisuje, jak vytvořit pozorovatele. Související téma [postupy: implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md), popisuje, jak vytvořit poskytovatele.  
  
### <a name="to-create-an-observer"></a>Chcete-li vytvořit pozorovatel  
  
1.  Definování pozorovatele, který je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Například následující kód definuje typ s názvem `TemperatureReporter` , který je vytvořený <xref:System.IObserver%601?displayProperty=nameWithType> implementace s argumentem obecného typu z `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Pokud pozorovatel můžete zastavit příjem oznámení před volání zprostředkovatele jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace, definujte privátní proměnnou, která bude obsahovat <xref:System.IDisposable> implementace vrácenou poskytovatele <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> – metoda. Také byste měli definovat metodu odběr, který volá zprostředkovatele <xref:System.IObservable%601.Subscribe%2A> metoda a úložišť vráceného <xref:System.IDisposable> objektu. Například následující kód definuje privátní proměnnou s názvem `unsubscriber` a definuje `Subscribe` metodu, která volá zprostředkovatele <xref:System.IObservable%601.Subscribe%2A> metoda a přiřadí vráceného objektu na `unsubscriber` proměnné.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Definujte metodu, která umožňuje pozorovatel k ukončení přijímání oznámení před volání zprostředkovatele jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace, pokud se tato funkce vyžaduje. Následující příklad definuje `Unsubscribe` metody.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Poskytují implementace tři metody určené <xref:System.IObserver%601> rozhraní: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. V závislosti na poskytovateli a potřebám vaší aplikace <xref:System.IObserver%601.OnError%2A> a <xref:System.IObserver%601.OnCompleted%2A> metody mohou být zástupné procedury implementace. Všimněte si, že <xref:System.IObserver%601.OnError%2A> metody by nemělo vyřizovat předaný <xref:System.Exception> objektu jako výjimku a <xref:System.IObserver%601.OnCompleted%2A> metoda je zdarma pro volání zprostředkovatele <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace. Následující příklad ukazuje <xref:System.IObserver%601> provádění `TemperatureReporter` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní zdrojový kód `TemperatureReporter` třídu, která poskytuje <xref:System.IObserver%601> implementace teploty monitorování aplikace.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IObserver%601>  
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)  
- [Postupy: Implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md)  
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
