---
title: Vnořená funkce nemá stejný podpis kompatibilní s delegátem '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591998"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="9a1ed-102">Vnořená funkce nemá stejný podpis kompatibilní s delegátem '\<vlastnost delegatename > "</span><span class="sxs-lookup"><span data-stu-id="9a1ed-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>
<span data-ttu-id="9a1ed-103">Výraz lambda se přiřadila do delegáta, který má nekompatibilní podpis.</span><span class="sxs-lookup"><span data-stu-id="9a1ed-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="9a1ed-104">Například v následujícím kódu, delegátu `Del` má dva celočíselné parametry.</span><span class="sxs-lookup"><span data-stu-id="9a1ed-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="9a1ed-105">Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarovaný jako typ `Del`:</span><span class="sxs-lookup"><span data-stu-id="9a1ed-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="9a1ed-106">**ID chyby:** BC36532</span><span class="sxs-lookup"><span data-stu-id="9a1ed-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a1ed-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9a1ed-107">To correct this error</span></span>  
  
- <span data-ttu-id="9a1ed-108">Úprava definice delegáta nebo přiřazené lambda výraz tak, aby podpisy jsou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="9a1ed-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1ed-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a1ed-109">See also</span></span>

- [<span data-ttu-id="9a1ed-110">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="9a1ed-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="9a1ed-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="9a1ed-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
