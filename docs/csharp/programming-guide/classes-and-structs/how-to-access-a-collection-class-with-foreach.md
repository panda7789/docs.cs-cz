---
title: "Postupy: Přístup ke třídě kolekce pomocí příkazu foreach (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="015b3-102">Postupy: Přístup ke třídě kolekce pomocí příkazu foreach (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="015b3-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="015b3-103">Následující příklad kódu ukazuje, jak napsat negenerická kolekce třídu, která lze použít s [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="015b3-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="015b3-104">Tento příklad definuje třídu tokenizátor řetězec.</span><span class="sxs-lookup"><span data-stu-id="015b3-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="015b3-105">V tomto příkladu představuje doporučený postup jenom v případě, že nelze použít třídu obecné kolekce.</span><span class="sxs-lookup"><span data-stu-id="015b3-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="015b3-106">Příklad toho, jak implementovat třídu obecné typově bezpečné kolekce, která podporuje <xref:System.Collections.Generic.IEnumerable%601>, najdete v části [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="015b3-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="015b3-107">V příkladu následující kód používá segmentu `Tokens` třídy pro přerušení větu "Toto je ukázkový věty."</span><span class="sxs-lookup"><span data-stu-id="015b3-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="015b3-108">do tokenů pomocí ' ' a '-' jako oddělovače.</span><span class="sxs-lookup"><span data-stu-id="015b3-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="015b3-109">Kód pak zobrazí tyto tokeny pomocí `foreach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="015b3-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="015b3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="015b3-110">Example</span></span>  
 <span data-ttu-id="015b3-111">Interně `Tokens` třída používá pole k uložení tokenů.</span><span class="sxs-lookup"><span data-stu-id="015b3-111">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="015b3-112">Vzhledem k tomu pole implementujete <xref:System.Collections.IEnumerator> a <xref:System.Collections.IEnumerable>, příklad kódu může použili metody pole – výčet (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, a <xref:System.Collections.IEnumerator.Current%2A>) místo nich definování `Tokens` – třída.</span><span class="sxs-lookup"><span data-stu-id="015b3-112">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="015b3-113">Metoda definice jsou zahrnuty v příkladu o vysvětlení, jak jsou definovány a co každý nemá.</span><span class="sxs-lookup"><span data-stu-id="015b3-113">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 <span data-ttu-id="015b3-114">V jazyce C#, není nutné pro třídu kolekce k implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> být kompatibilní s `foreach`.</span><span class="sxs-lookup"><span data-stu-id="015b3-114">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="015b3-115">Pokud třída nemá požadované <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, a <xref:System.Collections.IEnumerator.Current%2A> členy, bude fungovat s `foreach`.</span><span class="sxs-lookup"><span data-stu-id="015b3-115">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="015b3-116">Vynechání rozhraní nabízí výhodu v podobě umožňuje definovat návratový typ pro `Current` který je specifičtější než <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="015b3-116">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="015b3-117">To poskytuje bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="015b3-117">This provides type safety.</span></span>  
  
 <span data-ttu-id="015b3-118">Můžete například změňte následující řádky v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="015b3-118">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="015b3-119">Protože `Current` vrátí řetězec, kompilátor může rozpoznat, kdy se nekompatibilní typ se používá v `foreach` příkaz, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="015b3-119">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="015b3-120">Nevýhodou vynechání <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> je, že třída kolekce je už vzájemná spolupráce s `foreach` příkazy nebo ekvivalentní příkazy další běžné jazyků runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="015b3-120">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015b3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="015b3-121">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="015b3-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="015b3-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="015b3-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="015b3-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="015b3-124">Pole</span><span class="sxs-lookup"><span data-stu-id="015b3-124">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="015b3-125">Kolekce</span><span class="sxs-lookup"><span data-stu-id="015b3-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
