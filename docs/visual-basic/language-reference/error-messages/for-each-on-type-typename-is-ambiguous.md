---
title: '&#39;Pro každou&#39; typu &#39; &lt;typename&gt; &#39; je nejednoznačný, protože tento typ implementuje víc instancí &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456302"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="d53b1-102">&#39;Pro každou&#39; typu &#39; &lt;typename&gt; &#39; je nejednoznačný, protože tento typ implementuje víc instancí &#39;System.Collections.Generic.IEnumerable (Of T)&#39;</span><span class="sxs-lookup"><span data-stu-id="d53b1-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="d53b1-103">A `For Each` příkaz určuje, iterační proměnná, která má více než jednu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d53b1-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="d53b1-104">Proměnná iterátoru musí být typu, který implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní v jednom z `Collections` obory názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d53b1-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="d53b1-105">Je možné pro třídu pro implementaci více než jeden Konstruovaný obecný rozhraní použití jiného typu argumentu pro každý konstrukce.</span><span class="sxs-lookup"><span data-stu-id="d53b1-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="d53b1-106">Pokud třída, která se k tomu slouží k proměnné iterátoru, tato proměnná má více než jeden <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d53b1-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="d53b1-107">V takovém případě jazyka Visual Basic nelze zvolit která metoda se má volat.</span><span class="sxs-lookup"><span data-stu-id="d53b1-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="d53b1-108">**ID chyby:** BC32096</span><span class="sxs-lookup"><span data-stu-id="d53b1-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d53b1-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d53b1-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d53b1-110">Použít [DirectCast operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md) k přetypování typu proměnné iterátoru pro definování rozhraní <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="d53b1-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53b1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d53b1-111">See Also</span></span>  
 [<span data-ttu-id="d53b1-112">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d53b1-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="d53b1-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d53b1-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
