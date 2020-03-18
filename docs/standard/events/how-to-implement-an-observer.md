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
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="e52a1-102">Postupy: Implementace pozorovatele</span><span class="sxs-lookup"><span data-stu-id="e52a1-102">How to: Implement an Observer</span></span>
<span data-ttu-id="e52a1-103">Vzor návrhu pozorovatele vyžaduje rozdělení mezi pozorovatele, který registruje oznámení, a zprostředkovatelem, který sleduje data a odesílá oznámení jednomu nebo více pozorovatelům.</span><span class="sxs-lookup"><span data-stu-id="e52a1-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="e52a1-104">Toto téma popisuje, jak vytvořit pozorovatele.</span><span class="sxs-lookup"><span data-stu-id="e52a1-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="e52a1-105">Související [téma: Implementace zprostředkovatele](../../../docs/standard/events/how-to-implement-a-provider.md), popisuje, jak vytvořit zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e52a1-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="e52a1-106">Vytvoření pozorovatele</span><span class="sxs-lookup"><span data-stu-id="e52a1-106">To create an observer</span></span>  
  
1. <span data-ttu-id="e52a1-107">Definujte pozorovatele, což je typ, který implementuje <xref:System.IObserver%601?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e52a1-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="e52a1-108">Například následující kód definuje typ `TemperatureReporter` s názvem, <xref:System.IObserver%601?displayProperty=nameWithType> který je vyrobenou `Temperature`implementací s argumentem obecného typu .</span><span class="sxs-lookup"><span data-stu-id="e52a1-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="e52a1-109">Pokud pozorovatel může zastavit příjem oznámení před <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> zprostředkovatelvolá jeho provádění, definujte soukromou proměnnou, která bude obsahovat <xref:System.IDisposable> implementaci vrácenou metodou zprostředkovatele. <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e52a1-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e52a1-110">Měli byste také definovat metodu předplatného, <xref:System.IObservable%601.Subscribe%2A> která volá <xref:System.IDisposable> metodu zprostředkovatele a ukládá vrácený objekt.</span><span class="sxs-lookup"><span data-stu-id="e52a1-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="e52a1-111">Například následující kód definuje privátní proměnnou `unsubscriber` s názvem a definuje metodu, `Subscribe` která volá <xref:System.IObservable%601.Subscribe%2A> metodu zprostředkovatele a přiřadí vrácený objekt `unsubscriber` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e52a1-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="e52a1-112">Definujte metodu, která umožňuje pozorovateli zastavit příjem <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> oznámení před zprostředkovatelvolá jeho implementaci, pokud je tato funkce požadována.</span><span class="sxs-lookup"><span data-stu-id="e52a1-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="e52a1-113">Následující příklad definuje `Unsubscribe` metodu.</span><span class="sxs-lookup"><span data-stu-id="e52a1-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="e52a1-114">Uveďte implementace tří metod <xref:System.IObserver%601> definovaných <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>rozhraním: , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, a <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e52a1-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e52a1-115">V závislosti na zprostředkovatele a potřebách aplikace <xref:System.IObserver%601.OnError%2A> a <xref:System.IObserver%601.OnCompleted%2A> metody mohou být zástupné procedury implementace.</span><span class="sxs-lookup"><span data-stu-id="e52a1-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="e52a1-116">Všimněte <xref:System.IObserver%601.OnError%2A> si, že metoda <xref:System.Exception> by neměla zpracovávat předané objekt jako <xref:System.IObserver%601.OnCompleted%2A> <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> výjimku a metoda je zdarma volat implementaci zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e52a1-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="e52a1-117">Následující příklad ukazuje <xref:System.IObserver%601> implementaci `TemperatureReporter` třídy.</span><span class="sxs-lookup"><span data-stu-id="e52a1-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="e52a1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e52a1-118">Example</span></span>  
 <span data-ttu-id="e52a1-119">Následující příklad obsahuje úplný zdrojový `TemperatureReporter` kód pro třídu, která poskytuje <xref:System.IObserver%601> implementaci pro aplikaci pro sledování teploty.</span><span class="sxs-lookup"><span data-stu-id="e52a1-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="e52a1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e52a1-120">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="e52a1-121">Návrhový vzor Pozorovatel</span><span class="sxs-lookup"><span data-stu-id="e52a1-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)
- [<span data-ttu-id="e52a1-122">Postupy: Implementace poskytovatele</span><span class="sxs-lookup"><span data-stu-id="e52a1-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)
- [<span data-ttu-id="e52a1-123">Doporučené postupy pro návrhový vzor Pozorovatel</span><span class="sxs-lookup"><span data-stu-id="e52a1-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
