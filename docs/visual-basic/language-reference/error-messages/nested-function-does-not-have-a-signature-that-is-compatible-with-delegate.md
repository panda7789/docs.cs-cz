---
title: Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta &#39; &lt;vlastnost delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594468"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="34ba4-102">Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta &#39; &lt;vlastnost delegatename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="34ba4-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="34ba4-103">Výraz lambda byl přiřazen delegáta, který má nekompatibilní podpis.</span><span class="sxs-lookup"><span data-stu-id="34ba4-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="34ba4-104">Například následující kód, delegovat `Del` má dva parametry celé číslo.</span><span class="sxs-lookup"><span data-stu-id="34ba4-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="34ba4-105">Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarován jako typ `Del`:</span><span class="sxs-lookup"><span data-stu-id="34ba4-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="34ba4-106">**ID chyby:** BC36532</span><span class="sxs-lookup"><span data-stu-id="34ba4-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34ba4-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="34ba4-107">To correct this error</span></span>  
  
-   <span data-ttu-id="34ba4-108">Upravte definici delegáta nebo výrazu lambda přiřazené tak, aby byly kompatibilní podpisů.</span><span class="sxs-lookup"><span data-stu-id="34ba4-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ba4-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="34ba4-109">See Also</span></span>  
 [<span data-ttu-id="34ba4-110">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="34ba4-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="34ba4-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="34ba4-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
