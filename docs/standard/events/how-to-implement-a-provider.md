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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141553"
---
# <a name="how-to-implement-a-provider"></a>Postupy: Implementace poskytovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi poskytovatelem, který monitoruje data a odesílá oznámení a jedno nebo více pozorovatelů, kteří přijímají oznámení (zpětná volání) od poskytovatele. Toto téma popisuje, jak vytvořit poskytovatele. Související téma, [Postupy: implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md), popisuje, jak vytvořit pozorovatele.  
  
### <a name="to-create-a-provider"></a>Vytvoření zprostředkovatele  
  
1. Definujte data, která poskytovatel zodpovídá za odeslání pozorovatelům. I když poskytovatel a data, která odesílá pozorovatelům, mohou být jediný typ, jsou obvykle zastoupeny různými typy. Například v aplikaci pro monitorování teploty definuje struktura `Temperature` data, která poskytovatel (který je reprezentován třídou `TemperatureMonitor` definovanou v dalším kroku) monitoruje a ke kterým pozorovatelům se přihlašuje.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Definujte poskytovatele dat, což je typ, který implementuje rozhraní <xref:System.IObservable%601?displayProperty=nameWithType>. Obecný typ argumentu poskytovatele je typ, který poskytovatel odesílá pozorovatelům. Následující příklad definuje třídu `TemperatureMonitor`, což je vytvořená <xref:System.IObservable%601?displayProperty=nameWithType> implementace s argumentem obecného typu `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Určete, jak bude poskytovatel ukládat odkazy na pozorovatele, aby každý pozorovatel mohl být v případě potřeby upozorněn. Nejčastěji se pro tento účel používá objekt kolekce, například objekt generického <xref:System.Collections.Generic.List%601>. Následující příklad definuje privátní objekt <xref:System.Collections.Generic.List%601>, jehož instance je vytvořena v konstruktoru `TemperatureMonitor` třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Definujte <xref:System.IDisposable> implementaci, kterou může poskytovatel vrátit odběratelům, aby mohli kdykoli ukončit přijímání oznámení. Následující příklad definuje vnořenou `Unsubscriber` třídu, která je předána odkaz na kolekci předplatitelů a odběrateli při vytvoření instance třídy. Tento kód umožňuje předplatiteli volat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu pro odebrání sebe sama z kolekce předplatitelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implementujte metodu <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>. Metodě je předán odkaz na rozhraní <xref:System.IObserver%601?displayProperty=nameWithType> a měl by být uložen v objektu navrženém pro tento účel v kroku 3. Metoda by pak měla vrátit <xref:System.IDisposable> implementaci vyvinutou v kroku 4. Následující příklad ukazuje implementaci metody <xref:System.IObservable%601.Subscribe%2A> ve třídě `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Upozorněte pozorovatele podle potřeby tím, že zavolají jejich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace. V některých případech může zprostředkovatel volat metodu <xref:System.IObserver%601.OnError%2A>, když dojde k chybě. Například následující metoda `GetTemperature` simuluje monitorování, které každých pět sekund čte data o teplotě a upozorňuje pozorovatele, pokud se teplota změnila o alespoň 1 desetinnou úroveň od předchozího čtení. Pokud zařízení nehlásí teplotu (tj. Pokud má hodnotu null), zprostředkovatel upozorní pozorovatele, že je přenos dokončen. Všimněte si, že kromě toho, že voláním metody <xref:System.IObserver%601.OnCompleted%2A> pozorovatele, metoda `GetTemperature` vymaže kolekci <xref:System.Collections.Generic.List%601>. V tomto případě poskytovatel neprovede žádná volání metody <xref:System.IObserver%601.OnError%2A> pozorovatelům.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní zdrojový kód pro definování <xref:System.IObservable%601> implementace pro aplikaci monitorování teploty. Zahrnuje strukturu `Temperature`, což jsou data odesílaná pozorovatelům a třídu `TemperatureMonitor`, která je <xref:System.IObservable%601> implementace.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IObservable%601>
- [Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)
- [Postupy: Implementace pozorovatele](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern-best-practices.md)
