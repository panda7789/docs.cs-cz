---
title: Příkaz 'For Each' u typu '<typename>' je nejednoznačný, protože typ implementuje více instancí 'System.Collections.Generic.IEnumerable(Of T)'.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833383"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="99183-102">"For Each' u typu"\<typename >' je nejednoznačný, protože tento typ implementuje více instancí 'System.Collections.Generic.IEnumerable (Of T).</span><span class="sxs-lookup"><span data-stu-id="99183-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="99183-103">A `For Each` příkaz určuje, iterační proměnná, která má více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99183-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="99183-104">Proměnná iterátoru musí být typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní v jednom z `Collections` obory názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99183-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="99183-105">Je možné pro třídu pro implementaci více než jeden Konstruovaný obecný rozhraní použití jiného typu argumentu pro každý konstrukce.</span><span class="sxs-lookup"><span data-stu-id="99183-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="99183-106">Pokud třída, která se k tomu slouží k proměnné iterátoru, tato proměnná má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99183-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="99183-107">V takovém případě jazyka Visual Basic nelze zvolit která metoda se má volat.</span><span class="sxs-lookup"><span data-stu-id="99183-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="99183-108">**ID chyby:** BC32096</span><span class="sxs-lookup"><span data-stu-id="99183-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="99183-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="99183-109">To correct this error</span></span>  
  
-   <span data-ttu-id="99183-110">Použít [DirectCast operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) k přetypování typu proměnné iterátoru pro definování rozhraní <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="99183-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99183-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99183-111">See also</span></span>

- [<span data-ttu-id="99183-112">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="99183-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="99183-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="99183-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
