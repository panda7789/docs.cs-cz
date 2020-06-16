---
title: 'Postupy: Implementace pozorovatele'
description: Implementujte pozorovatele v .NET. Návrhový vzor pozorovatele vyžaduje rozdělení mezi pozorovatelem, který registruje pro oznámení a poskytovatelem.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 43236ead15be0777f4284ba553a2f2f5e09d0a73
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768992"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="64d46-104">Postupy: Implementace pozorovatele</span><span class="sxs-lookup"><span data-stu-id="64d46-104">How to: Implement an Observer</span></span>
<span data-ttu-id="64d46-105">Vzor návrhu pozorovatele vyžaduje rozdělení mezi pozorovatelem, který registruje oznámení, a poskytovatelem, který monitoruje data a odesílá oznámení jednomu nebo více pozorovatelům.</span><span class="sxs-lookup"><span data-stu-id="64d46-105">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="64d46-106">Toto téma popisuje, jak vytvořit pozorovatele.</span><span class="sxs-lookup"><span data-stu-id="64d46-106">This topic discusses how to create an observer.</span></span> <span data-ttu-id="64d46-107">Související téma, [Postupy: implementace poskytovatele](how-to-implement-a-provider.md), popisuje, jak vytvořit poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="64d46-107">A related topic, [How to: Implement a Provider](how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="64d46-108">Vytvoření pozorovatele</span><span class="sxs-lookup"><span data-stu-id="64d46-108">To create an observer</span></span>  
  
1. <span data-ttu-id="64d46-109">Definujte pozorovatele, což je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64d46-109">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="64d46-110">Například následující kód definuje typ s názvem `TemperatureReporter` , který je vytvořenou <xref:System.IObserver%601?displayProperty=nameWithType> implementací s argumentem obecného typu `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="64d46-110">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="64d46-111">Pokud pozorovatel může zastavit příjem oznámení předtím, než poskytovatel zavolá svou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementaci, definujte privátní proměnnou, která bude obsahovat <xref:System.IDisposable> implementaci vrácenou <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodou poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="64d46-111">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="64d46-112">Měli byste také definovat metodu předplatného, která volá <xref:System.IObservable%601.Subscribe%2A> metodu poskytovatele a uloží vrácený <xref:System.IDisposable> objekt.</span><span class="sxs-lookup"><span data-stu-id="64d46-112">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="64d46-113">Například následující kód definuje soukromou proměnnou s názvem `unsubscriber` a definuje `Subscribe` metodu, která volá <xref:System.IObservable%601.Subscribe%2A> metodu poskytovatele a přiřadí vrácený objekt `unsubscriber` proměnné.</span><span class="sxs-lookup"><span data-stu-id="64d46-113">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="64d46-114">Definujte metodu, která pozorovateli umožní zastavit příjem oznámení předtím, než poskytovatel zavolá jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementaci, pokud je tato funkce povinná.</span><span class="sxs-lookup"><span data-stu-id="64d46-114">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="64d46-115">Následující příklad definuje `Unsubscribe` metodu.</span><span class="sxs-lookup"><span data-stu-id="64d46-115">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="64d46-116">Poskytněte implementace tří metod definovaných <xref:System.IObserver%601> rozhraním: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="64d46-116">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64d46-117">V závislosti na poskytovateli a potřebách aplikace <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> mohou být metody a v zástupných implementacích.</span><span class="sxs-lookup"><span data-stu-id="64d46-117">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="64d46-118">Všimněte si, že <xref:System.IObserver%601.OnError%2A> Metoda by neměla zpracovávat předaný <xref:System.Exception> objekt jako výjimku a <xref:System.IObserver%601.OnCompleted%2A> Metoda je bezplatná pro volání <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="64d46-118">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="64d46-119">Následující příklad ukazuje <xref:System.IObserver%601> implementaci `TemperatureReporter` třídy.</span><span class="sxs-lookup"><span data-stu-id="64d46-119">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="64d46-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="64d46-120">Example</span></span>  
 <span data-ttu-id="64d46-121">Následující příklad obsahuje úplný zdrojový kód pro `TemperatureReporter` třídu, která poskytuje <xref:System.IObserver%601> implementaci pro aplikaci monitorování teploty.</span><span class="sxs-lookup"><span data-stu-id="64d46-121">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="64d46-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="64d46-122">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="64d46-123">Vzor návrhu pozorovatele</span><span class="sxs-lookup"><span data-stu-id="64d46-123">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="64d46-124">Postupy: implementace poskytovatele</span><span class="sxs-lookup"><span data-stu-id="64d46-124">How to: Implement a Provider</span></span>](how-to-implement-a-provider.md)
- [<span data-ttu-id="64d46-125">Doporučené postupy pro návrhový vzor Pozorovatel</span><span class="sxs-lookup"><span data-stu-id="64d46-125">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
