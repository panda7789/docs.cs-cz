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
ms.openlocfilehash: 4f8a213c0df3ef3c633106b7249a4947fe77c0d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280020"
---
# <a name="how-to-implement-a-provider"></a>Postupy: Implementace poskytovatele
Vzor návrhu pozorovatele vyžaduje rozdělení mezi poskytovatelem, který monitoruje data a odesílá oznámení a jedno nebo více pozorovatelů, kteří přijímají oznámení (zpětná volání) od poskytovatele. Toto téma popisuje, jak vytvořit poskytovatele. Související téma, [Postupy: implementace pozorovatele](how-to-implement-an-observer.md), popisuje, jak vytvořit pozorovatele.  
  
### <a name="to-create-a-provider"></a>Vytvoření zprostředkovatele  
  
1. Definujte data, která poskytovatel zodpovídá za odeslání pozorovatelům. I když poskytovatel a data, která odesílá pozorovatelům, mohou být jediný typ, jsou obvykle zastoupeny různými typy. Například v aplikaci pro monitorování teploty `Temperature` definuje struktura data, která poskytovatel (který je reprezentován `TemperatureMonitor` třídou definovanou v dalším kroku) monitoruje a ke kterým pozorovatelům se přihlašuje.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Definujte poskytovatele dat, což je typ, který implementuje <xref:System.IObservable%601?displayProperty=nameWithType> rozhraní. Obecný typ argumentu poskytovatele je typ, který poskytovatel odesílá pozorovatelům. Následující příklad definuje `TemperatureMonitor` třídu, která je konstruovánou <xref:System.IObservable%601?displayProperty=nameWithType> implementací s argumentem obecného typu `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Určete, jak bude poskytovatel ukládat odkazy na pozorovatele, aby každý pozorovatel mohl být v případě potřeby upozorněn. Nejčastěji se pro tento účel používá objekt kolekce, například obecný <xref:System.Collections.Generic.List%601> objekt. Následující příklad definuje privátní <xref:System.Collections.Generic.List%601> objekt, který je vytvořen v `TemperatureMonitor` konstruktoru třídy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Definujte <xref:System.IDisposable> implementaci, kterou může poskytovatel vrátit odběratelům, aby mohli kdykoli ukončit příjem oznámení. Následující příklad definuje vnořenou `Unsubscriber` třídu, která je předána odkaz na kolekci předplatitelů a odběrateli při vytvoření instance třídy. Tento kód umožňuje předplatiteli volat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu pro odebrání sebe sama z kolekce předplatitelů.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implementujte <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodu. Metodě je předán odkaz na <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní a měl by být uložen v objektu navrženém pro tento účel v kroku 3. Metoda by pak měla vrátit <xref:System.IDisposable> implementaci vyvinutou v kroku 4. Následující příklad ukazuje implementaci <xref:System.IObservable%601.Subscribe%2A> metody ve `TemperatureMonitor` třídě.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Upozorněte pozorovatele podle potřeby tím, že zavolají jejich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> implementace, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . V některých případech může zprostředkovatel volat <xref:System.IObserver%601.OnError%2A> metodu, když dojde k chybě. Následující `GetTemperature` Metoda například simuluje monitorování, které každých pět sekund čte data o teplotě a upozorňuje na pozorovatele, pokud se teplota změnila o nejméně 1 desetinnou měrou od předchozího čtení. Pokud zařízení nehlásí teplotu (tj. Pokud má hodnotu null), zprostředkovatel upozorní pozorovatele, že je přenos dokončen. Všimněte si, že kromě volání jednotlivých metod pozorovatele <xref:System.IObserver%601.OnCompleted%2A> `GetTemperature` Metoda vymaže <xref:System.Collections.Generic.List%601> kolekci. V tomto případě poskytovatel neprovede žádná volání <xref:System.IObserver%601.OnError%2A> metody pozorovatele.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje úplný zdrojový kód pro definování <xref:System.IObservable%601> implementace pro aplikaci monitorování teploty. Obsahuje `Temperature` strukturu, která je data odesílaná pozorovatelům a `TemperatureMonitor` třídu, která je <xref:System.IObservable%601> implementací.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IObservable%601>
- [Vzor návrhu pozorovatele](observer-design-pattern.md)
- [Postupy: implementace pozorovatele](how-to-implement-an-observer.md)
- [Doporučené postupy pro návrhový vzor Pozorovatel](observer-design-pattern-best-practices.md)
