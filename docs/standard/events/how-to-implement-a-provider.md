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
ms.openlocfilehash: f5bb3cda0caa39ba3fd094b80e0b769a4bfc1f85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141553"
---
# <a name="how-to-implement-a-provider"></a>Postupy: Implementace poskytovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi zprostředkovatele, který monitoruje data a odesílá oznámení, a jedním nebo více pozorovateli, kteří přijímají oznámení (zpětná volání) od zprostředkovatele. Toto téma popisuje, jak vytvořit zprostředkovatele. Související [téma: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md), popisuje, jak vytvořit pozorovatele.  
  
### <a name="to-create-a-provider"></a>Vytvoření zprostředkovatele  
  
1. Definujte data, za která je poskytovatel odpovědný za odesílání pozorovatelům. Přestože zprostředkovatel a data, která odesílá pozorovatelům může být jeden typ, jsou obecně reprezentovány různými typy. Například v aplikaci pro `Temperature` monitorování teploty struktura definuje data, která zprostředkovatel `TemperatureMonitor` (který je reprezentován třídou definovanou v dalším kroku) monitoruje a ke kterým pozorovatelům se přihlásí.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Definujte zprostředkovatele dat, což je <xref:System.IObservable%601?displayProperty=nameWithType> typ, který implementuje rozhraní. Argument obecného typu zprostředkovatele je typ, který zprostředkovatel odesílá pozorovatelům. Následující příklad definuje `TemperatureMonitor` třídu, což je <xref:System.IObservable%601?displayProperty=nameWithType> vytvořená implementace s `Temperature`argumentem obecného typu .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Určete, jak bude zprostředkovatel ukládat odkazy na pozorovatele, aby každý pozorovatel mohl být v případě potřeby upozorněn. Nejčastěji se k tomuto účelu <xref:System.Collections.Generic.List%601> používá objekt kolekce, například obecný objekt. Následující příklad definuje soukromý <xref:System.Collections.Generic.List%601> objekt, který je vytvořen `TemperatureMonitor` v konstruktoru třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Definujte <xref:System.IDisposable> implementaci, kterou může zprostředkovatel vrátit odběratelům, aby mohli kdykoli přestat přijímat oznámení. Následující příklad definuje vnořené `Unsubscriber` třídy, která je předána odkaz na kolekci odběratelů a odběratel, když je vytvořena instance třídy. Tento kód umožňuje odběrateli volat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu odebrat sám z kolekce předplatitelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implementujte <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodu. Metoda je předán odkaz <xref:System.IObserver%601?displayProperty=nameWithType> na rozhraní a by měly být uloženy v objektu určené pro tento účel v kroku 3. Metoda by pak <xref:System.IDisposable> měla vrátit implementaci vyvinutou v kroku 4. Následující příklad ukazuje implementaci <xref:System.IObservable%601.Subscribe%2A> metody ve `TemperatureMonitor` třídě.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Uvědomte pozorovatele podle <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>potřeby <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> voláním jejich , a implementace. V některých případech zprostředkovatel nemusí <xref:System.IObserver%601.OnError%2A> volat metodu, když dojde k chybě. Například následující `GetTemperature` metoda simuluje monitor, který čte údaje o teplotě každých pět sekund a upozorní pozorovatele, pokud se teplota změnila nejméně o 0,1 stupně od předchozího čtení. Pokud zařízení nehlásí teplotu (to znamená, pokud je jeho hodnota null), poskytovatel upozorní pozorovatele, že přenos je dokončen. Všimněte si, že kromě volání <xref:System.IObserver%601.OnCompleted%2A> metody `GetTemperature` každého pozorovatele <xref:System.Collections.Generic.List%601> metoda vymaže kolekce. V tomto případě zprostředkovatel neprovede <xref:System.IObserver%601.OnError%2A> žádné volání metody svých pozorovatelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní zdrojový kód <xref:System.IObservable%601> pro definování implementace pro aplikaci sledování teploty. Zahrnuje `Temperature` strukturu, což jsou data odeslaná pozorovatelům, a třídu, `TemperatureMonitor` což je <xref:System.IObservable%601> implementace.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IObservable%601>
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
