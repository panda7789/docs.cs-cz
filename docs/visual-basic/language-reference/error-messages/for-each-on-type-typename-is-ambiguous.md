---
title: Příkaz 'For Each' u typu '<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402963"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="ed364-102">Příkaz 'For Each' u typu '\<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.</span><span class="sxs-lookup"><span data-stu-id="ed364-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="ed364-103">`For Each`Příkaz určuje proměnnou iterátoru, která má více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ed364-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="ed364-104">Proměnná iterátoru musí být typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo v jednom z `Collections` oborů názvů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed364-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="ed364-105">Je možné, že třída implementuje více než jedno konstruované obecné rozhraní s použitím jiného argumentu typu pro každou konstrukci.</span><span class="sxs-lookup"><span data-stu-id="ed364-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="ed364-106">Pokud se třída, která to dělá, používá pro proměnnou iterátoru, má tato proměnná více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="ed364-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="ed364-107">V takovém případě Visual Basic nemůže zvolit metodu volání.</span><span class="sxs-lookup"><span data-stu-id="ed364-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="ed364-108">**ID chyby:** BC32096</span><span class="sxs-lookup"><span data-stu-id="ed364-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed364-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ed364-109">To correct this error</span></span>  
  
- <span data-ttu-id="ed364-110">Použijte [operátor DirectCast](../operators/directcast-operator.md) nebo [operátor TryCast](../operators/trycast-operator.md) pro přetypování typu proměnné iterátoru na rozhraní definující <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="ed364-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed364-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed364-111">See also</span></span>

- [<span data-ttu-id="ed364-112">For Each...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="ed364-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="ed364-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed364-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
