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
ms.openlocfilehash: 969b83bcd11159509a2cc1ed843836679ffd1705
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289717"
---
# <a name="how-to-implement-an-observer"></a>Postupy: Implementace pozorovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi pozorovatelem, který registruje oznámení, a poskytovatelem, který monitoruje data a odesílá oznámení jednomu nebo více pozorovatelům. Toto téma popisuje, jak vytvořit pozorovatele. Související téma, [Postupy: implementace poskytovatele](how-to-implement-a-provider.md), popisuje, jak vytvořit poskytovatele.  
  
### <a name="to-create-an-observer"></a>Vytvoření pozorovatele  
  
1. Definujte pozorovatele, což je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní. Například následující kód definuje typ s názvem `TemperatureReporter` , který je vytvořenou <xref:System.IObserver%601?displayProperty=nameWithType> implementací s argumentem obecného typu `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Pokud pozorovatel může zastavit příjem oznámení předtím, než poskytovatel zavolá svou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementaci, definujte privátní proměnnou, která bude obsahovat <xref:System.IDisposable> implementaci vrácenou <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodou poskytovatele. Měli byste také definovat metodu předplatného, která volá <xref:System.IObservable%601.Subscribe%2A> metodu poskytovatele a uloží vrácený <xref:System.IDisposable> objekt. Například následující kód definuje soukromou proměnnou s názvem `unsubscriber` a definuje `Subscribe` metodu, která volá <xref:System.IObservable%601.Subscribe%2A> metodu poskytovatele a přiřadí vrácený objekt `unsubscriber` proměnné.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Definujte metodu, která pozorovateli umožní zastavit příjem oznámení předtím, než poskytovatel zavolá jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementaci, pokud je tato funkce povinná. Následující příklad definuje `Unsubscribe` metodu.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Poskytněte implementace tří metod definovaných <xref:System.IObserver%601> rozhraním: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . V závislosti na poskytovateli a potřebách aplikace <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> mohou být metody a v zástupných implementacích. Všimněte si, že <xref:System.IObserver%601.OnError%2A> Metoda by neměla zpracovávat předaný <xref:System.Exception> objekt jako výjimku a <xref:System.IObserver%601.OnCompleted%2A> Metoda je bezplatná pro volání <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace poskytovatele. Následující příklad ukazuje <xref:System.IObserver%601> implementaci `TemperatureReporter` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje úplný zdrojový kód pro `TemperatureReporter` třídu, která poskytuje <xref:System.IObserver%601> implementaci pro aplikaci monitorování teploty.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IObserver%601>
- [Vzor návrhu pozorovatele](observer-design-pattern.md)
- [Postupy: implementace poskytovatele](how-to-implement-a-provider.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](observer-design-pattern-best-practices.md)
