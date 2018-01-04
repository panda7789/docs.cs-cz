---
title: 'Postupy: Implementace pozorovatele'
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b895739daf1f4844d6300df4788441be67b90254
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="32b4c-102">Postupy: Implementace pozorovatele</span><span class="sxs-lookup"><span data-stu-id="32b4c-102">How to: Implement an Observer</span></span>
<span data-ttu-id="32b4c-103">Návrhový vzor pozorovatel vyžaduje rozdělení pozorovatele, které je zaregistruje pro oznámení, a zprostředkovatele, který monitoruje data a odešle oznámení pozorovatelů jeden nebo více.</span><span class="sxs-lookup"><span data-stu-id="32b4c-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="32b4c-104">Toto téma popisuje postup vytvoření pozorovatele.</span><span class="sxs-lookup"><span data-stu-id="32b4c-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="32b4c-105">Související téma, [postupy: implementace poskytovatele](../../../docs/standard/events/how-to-implement-a-provider.md), popisuje, jak vytvářet poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="32b4c-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="32b4c-106">Chcete-li vytvořit pozorovatele</span><span class="sxs-lookup"><span data-stu-id="32b4c-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="32b4c-107">Definování pozorovatel, což je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="32b4c-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="32b4c-108">Například následující kód definuje typ s názvem `TemperatureReporter` který je vytvořený <xref:System.IObserver%601?displayProperty=nameWithType> implementace s argumentem obecného typu ve `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="32b4c-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="32b4c-109">Pokud pozorovatel zastavit příjem oznámení před volání zprostředkovatele jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace definovat soukromé proměnné, která bude obsahovat <xref:System.IDisposable> implementace vrácený poskytovatele <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="32b4c-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="32b4c-110">Měli byste také definovat předplatné metodu, která volá metody poskytovatele <xref:System.IObservable%601.Subscribe%2A> metoda a úložišť vrácený <xref:System.IDisposable> objektu.</span><span class="sxs-lookup"><span data-stu-id="32b4c-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="32b4c-111">Například následující kód definuje soukromé proměnné s názvem `unsubscriber` a definuje `Subscribe` metoda, která volá metody poskytovatele <xref:System.IObservable%601.Subscribe%2A> metoda a přiřadí vrácený objekt, který má `unsubscriber` proměnné.</span><span class="sxs-lookup"><span data-stu-id="32b4c-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="32b4c-112">Zadejte metodu, která umožňuje pozorovatel zastavit přijímání oznámení před volání zprostředkovatele jeho <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementace, pokud je tato funkce se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="32b4c-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="32b4c-113">V následujícím příkladu definuje `Unsubscribe` metoda.</span><span class="sxs-lookup"><span data-stu-id="32b4c-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="32b4c-114">Poskytovat implementace tři metody definované <xref:System.IObserver%601> rozhraní: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32b4c-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32b4c-115">V závislosti na zprostředkovateli a potřebám aplikace <xref:System.IObserver%601.OnError%2A> a <xref:System.IObserver%601.OnCompleted%2A> metody může být implementace se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="32b4c-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="32b4c-116">Všimněte si, že <xref:System.IObserver%601.OnError%2A> metoda by nemělo vyřizovat předaný <xref:System.Exception> objektu jako výjimka a <xref:System.IObserver%601.OnCompleted%2A> metoda je bezplatná volání poskytovatele <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="32b4c-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="32b4c-117">Následující příklad ukazuje <xref:System.IObserver%601> implementace `TemperatureReporter` třídy.</span><span class="sxs-lookup"><span data-stu-id="32b4c-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="32b4c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="32b4c-118">Example</span></span>  
 <span data-ttu-id="32b4c-119">Následující příklad obsahuje kompletní zdrojový kód `TemperatureReporter` třídy, která poskytuje <xref:System.IObserver%601> implementace teplotě monitorování aplikace.</span><span class="sxs-lookup"><span data-stu-id="32b4c-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="32b4c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="32b4c-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="32b4c-121">Návrhový vzor Pozorovatel</span><span class="sxs-lookup"><span data-stu-id="32b4c-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="32b4c-122">Postupy: Implementace poskytovatele</span><span class="sxs-lookup"><span data-stu-id="32b4c-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="32b4c-123">Doporučené postupy pro návrhový vzor Pozorovatel</span><span class="sxs-lookup"><span data-stu-id="32b4c-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
