---
title: "Propojené operace"
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
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10c1188820b7a270baa0c51696974f93a8a2990
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="interlocked-operations"></a><span data-ttu-id="4d405-102">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="4d405-102">Interlocked Operations</span></span>
<span data-ttu-id="4d405-103"><xref:System.Threading.Interlocked> Třída poskytuje metody, které se synchronizují přístup k proměnné, která je sdílen více vláken.</span><span class="sxs-lookup"><span data-stu-id="4d405-103">The <xref:System.Threading.Interlocked> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="4d405-104">Podprocesy různé procesy můžete použít tento mechanismus, pokud je proměnná ve sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="4d405-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="4d405-105">Propojené operace jsou atomic – celou operaci je jednotkou, která nelze přerušit jinou operací interlocked na stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="4d405-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another interlocked operation on the same variable.</span></span> <span data-ttu-id="4d405-106">To je důležité v operačních systémech s preemptivní více vláken, kde můžete vlákna pozastaví po načtení hodnotu z adresy paměti, ale před spojením šanci na změnu a uložte ho.</span><span class="sxs-lookup"><span data-stu-id="4d405-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="4d405-107"><xref:System.Threading.Interlocked> Třída poskytuje následující operace:</span><span class="sxs-lookup"><span data-stu-id="4d405-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="4d405-108">V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda přidá celočíselnou hodnotu do proměnné a vrátí novou hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="4d405-108">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="4d405-109">V rozhraní .NET Framework verze 2.0 <xref:System.Threading.Interlocked.Read%2A> metoda čte 64bitové celé číslo hodnotu jako atomickou operaci.</span><span class="sxs-lookup"><span data-stu-id="4d405-109">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Read%2A> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="4d405-110">To je užitečné na 32bitové operační systémy, kde čtení 64bitové celé číslo není normálně atomické operace.</span><span class="sxs-lookup"><span data-stu-id="4d405-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="4d405-111"><xref:System.Threading.Interlocked.Increment%2A> a <xref:System.Threading.Interlocked.Decrement%2A> metody zvýší nebo sníží proměnné a vrátí výslednou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d405-111">The <xref:System.Threading.Interlocked.Increment%2A> and <xref:System.Threading.Interlocked.Decrement%2A> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="4d405-112"><xref:System.Threading.Interlocked.Exchange%2A> Metoda provádí atomic výměny hodnotu do proměnné, vrátí tuto hodnotu a nahraďte ji s novou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4d405-112">The <xref:System.Threading.Interlocked.Exchange%2A> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="4d405-113">V rozhraní .NET Framework verze 2.0 obecný přetížení této metody slouží k provedení této exchange na proměnnou libovolného typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="4d405-113">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="4d405-114">V tématu <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="4d405-114">See <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span></span>  
  
-   <span data-ttu-id="4d405-115"><xref:System.Threading.Interlocked.CompareExchange%2A> Metoda také výměny dvě hodnoty, ale contingent u výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="4d405-115">The <xref:System.Threading.Interlocked.CompareExchange%2A> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="4d405-116">V rozhraní .NET Framework verze 2.0 obecný přetížení této metody slouží k provedení této exchange na proměnnou libovolného typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="4d405-116">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="4d405-117">V tématu <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="4d405-117">See <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span></span>  
  
 <span data-ttu-id="4d405-118">U moderní procesorů, metody <xref:System.Threading.Interlocked> třída může být implementována často jeden instrukcí.</span><span class="sxs-lookup"><span data-stu-id="4d405-118">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="4d405-119">Proto poskytují velmi výkonné synchronizace a jde použít k sestavení vyšší úrovně synchronizace mechanismy, jako typu číselník zámky.</span><span class="sxs-lookup"><span data-stu-id="4d405-119">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="4d405-120">Pro příklad, který používá <xref:System.Threading.Monitor> a <xref:System.Threading.Interlocked> třídy v kombinaci, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="4d405-120">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see [Monitors](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="4d405-121">Příklad CompareExchange</span><span class="sxs-lookup"><span data-stu-id="4d405-121">CompareExchange Example</span></span>  
 <span data-ttu-id="4d405-122"><xref:System.Threading.Interlocked.CompareExchange%2A> Metoda slouží k ochraně výpočtů, u kterých jsou složitější než jednoduché přírůstek a snížení.</span><span class="sxs-lookup"><span data-stu-id="4d405-122">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="4d405-123">Následující příklad ukazuje metodu bezpečné pro přístup z více vláken, která přidá do Mezisoučet uložené jako plovoucí bodu číslo.</span><span class="sxs-lookup"><span data-stu-id="4d405-123">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="4d405-124">(Pro celá čísla, <xref:System.Threading.Interlocked.Add%2A> metoda je jednodušší řešení.) Kompletní kód příklady najdete v tématu přetížení <xref:System.Threading.Interlocked.CompareExchange%2A> které přebírají jednoduchou přesností a dvojitou přesností s plovoucí desetinnou čárkou argumenty (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> a <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span><span class="sxs-lookup"><span data-stu-id="4d405-124">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="4d405-125">Netypové přetížení systému Exchange a CompareExchange</span><span class="sxs-lookup"><span data-stu-id="4d405-125">Untyped Overloads of Exchange and CompareExchange</span></span>  
 <span data-ttu-id="4d405-126"><xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody, mají přetížení, které nepřebírají argumenty typu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4d405-126">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="4d405-127">První argument každého z těchto přetížení je `ref Object` (`ByRef … As Object` v jazyce Visual Basic), a bezpečnost typů vyžaduje proměnnou předaný tento argument výhradně zadat jako <xref:System.Object>; nejde jednoduše přetypovat na typ první argument <xref:System.Object> Při volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="4d405-127">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d405-128">V rozhraní .NET Framework verze 2.0, použijte obecné přetížení <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody pro výměnu silně typované proměnné.</span><span class="sxs-lookup"><span data-stu-id="4d405-128">In the .NET Framework version 2.0, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="4d405-129">Následující příklad kódu ukazuje vlastnost typu `ClassA` , lze nastavit pouze jednou, jak může být implementované v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="4d405-129">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4d405-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d405-130">See Also</span></span>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="4d405-131">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="4d405-131">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="4d405-132">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="4d405-132">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
