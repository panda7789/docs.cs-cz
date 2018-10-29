---
title: Propojené operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f96286da84e41e79fb0b6253d6f20eea89da21a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201348"
---
# <a name="interlocked-operations"></a><span data-ttu-id="a54ee-102">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="a54ee-102">Interlocked operations</span></span>

<span data-ttu-id="a54ee-103"><xref:System.Threading.Interlocked?displayProperty=nameWithType> Třída poskytuje metody, které se synchronizují přístup k proměnné, které jsou sdíleny více vlákny.</span><span class="sxs-lookup"><span data-stu-id="a54ee-103">The <xref:System.Threading.Interlocked?displayProperty=nameWithType> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="a54ee-104">Vlákna různé postupy můžete použít tento mechanismus, pokud je proměnná ve sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="a54ee-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="a54ee-105">Propojené operace jsou atomické – to znamená, celá operace je jednotka, která se nedá přerušit jinou operací u stejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="a54ee-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another operation on the same variable.</span></span> <span data-ttu-id="a54ee-106">To je důležité v operačních systémech s preemptive multithreadingu, kde můžete vlákna pozastaví po načtení hodnoty z adresy paměti, ale před máte možnost ji změnit a uložte ho.</span><span class="sxs-lookup"><span data-stu-id="a54ee-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="a54ee-107"><xref:System.Threading.Interlocked> Třída poskytuje následující operace:</span><span class="sxs-lookup"><span data-stu-id="a54ee-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="a54ee-108"><xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> Metoda přidá celočíselnou hodnotu do proměnné a vrátí novou hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="a54ee-108">The <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="a54ee-109"><xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> Metoda čte 64bitové celé číslo hodnotu jako atomickou operaci.</span><span class="sxs-lookup"><span data-stu-id="a54ee-109">The <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="a54ee-110">To je užitečné v 32bitové operační systémy, kde čtení 64-bit integer není obvykle atomické operace.</span><span class="sxs-lookup"><span data-stu-id="a54ee-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="a54ee-111"><xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> a <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> metody zvýšení nebo snížení proměnné a vrátí výslednou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a54ee-111">The <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> and <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="a54ee-112"><xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> Metoda provádí atomické výměny hodnotu do proměnné, vrátí tuto hodnotu a jeho nahrazení atributem novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a54ee-112">The <xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="a54ee-113">Použití obecného <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> přetížení této metody k provedení exchange u proměnné jakéhokoliv odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="a54ee-113">Use a generic <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> overload of this method to perform the exchange on a variable of any reference type.</span></span>  
  
-   <span data-ttu-id="a54ee-114"><xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> Metoda také vymění dvě hodnoty, ale závislé na výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="a54ee-114">The <xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="a54ee-115">Použití obecného <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> přetížení této metody k provedení exchange u proměnné jakéhokoliv odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="a54ee-115">Use a generic <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> overload of this method to perform the exchange on a variable of any reference type.</span></span>  
  
 <span data-ttu-id="a54ee-116">Na moderních procesory, metody <xref:System.Threading.Interlocked> třídy může být implementována často jediná instrukce.</span><span class="sxs-lookup"><span data-stu-id="a54ee-116">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="a54ee-117">Proto poskytují velmi výkonné synchronizace a je možné vytvářet vyšší úrovně mechanismy synchronizace, otočný zámky, jako je.</span><span class="sxs-lookup"><span data-stu-id="a54ee-117">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="a54ee-118">Příklad, který se používá <xref:System.Threading.Monitor> a <xref:System.Threading.Interlocked> naleznete v tématu třídy v kombinaci, <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="a54ee-118">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="a54ee-119">Příklad CompareExchange</span><span class="sxs-lookup"><span data-stu-id="a54ee-119">CompareExchange example</span></span>

 <span data-ttu-id="a54ee-120"><xref:System.Threading.Interlocked.CompareExchange%2A> Metodu lze použít k ochraně výpočty, které jsou složitější než jednoduché Inkrementace a dekrementace.</span><span class="sxs-lookup"><span data-stu-id="a54ee-120">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="a54ee-121">Následující příklad ukazuje metodu bezpečným pro vlákno, které přidají průběžný celkový součet uložené jako plovoucí číslo bodu.</span><span class="sxs-lookup"><span data-stu-id="a54ee-121">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="a54ee-122">(Pro celá čísla, <xref:System.Threading.Interlocked.Add%2A> metoda je jednodušší řešení.) Kompletní kód příkladů, naleznete v tématu přetížení <xref:System.Threading.Interlocked.CompareExchange%2A> , která přijímá argumenty jednoduchou přesností a dvojité přesnosti s plovoucí desetinnou čárkou (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> a <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span><span class="sxs-lookup"><span data-stu-id="a54ee-122">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="a54ee-123">Netypové přetížení systému Exchange a CompareExchange</span><span class="sxs-lookup"><span data-stu-id="a54ee-123">Untyped overloads of Exchange and CompareExchange</span></span>

 <span data-ttu-id="a54ee-124"><xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody mají přetížení, která přijímají argumenty typu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a54ee-124">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="a54ee-125">Prvním argumentem funkce všech tato přetížení je `ref Object` (`ByRef … As Object` v jazyce Visual Basic), a bezpečnost typů vyžaduje proměnnou předat tento argument být typu striktně <xref:System.Object>; nelze jednoduše převést na typ prvního argumentu <xref:System.Object> Při volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="a54ee-125">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a54ee-126">V rozhraní .NET Framework verze 2.0 nebo novější, použijte obecné přetížení <xref:System.Threading.Interlocked.Exchange%2A> a <xref:System.Threading.Interlocked.CompareExchange%2A> metody k výměně silně typované proměnné.</span><span class="sxs-lookup"><span data-stu-id="a54ee-126">In the .NET Framework version 2.0 and later, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="a54ee-127">Následující příklad kódu ukazuje vlastnost typu `ClassA` , které lze nastavit pouze jednou, protože může být implementováno v rozhraní .NET Framework verze 1.0 nebo 1.1.</span><span class="sxs-lookup"><span data-stu-id="a54ee-127">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a54ee-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a54ee-128">See also</span></span>

- <xref:System.Threading.Interlocked?displayProperty=nameWithType>  
- <xref:System.Threading.Monitor?displayProperty=nameWithType>  
- [<span data-ttu-id="a54ee-129">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="a54ee-129">Threading</span></span>](index.md)  
- [<span data-ttu-id="a54ee-130">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="a54ee-130">Threading objects and features</span></span>](threading-objects-and-features.md)
