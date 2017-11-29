---
title: "Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta & č. 39; &lt;vlastnost delegatename&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="b5aa0-102">Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta & č. 39; &lt;vlastnost delegatename&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="b5aa0-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="b5aa0-103">Výraz lambda byl přiřazen delegáta, který má nekompatibilní podpis.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="b5aa0-104">Například následující kód, delegovat `Del` má dva parametry celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="b5aa0-105">Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarován jako typ `Del`:</span><span class="sxs-lookup"><span data-stu-id="b5aa0-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="b5aa0-106">**ID chyby:** BC36532</span><span class="sxs-lookup"><span data-stu-id="b5aa0-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5aa0-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b5aa0-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b5aa0-108">Upravte definici delegáta nebo výrazu lambda přiřazené tak, aby byly kompatibilní podpisů.</span><span class="sxs-lookup"><span data-stu-id="b5aa0-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5aa0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5aa0-109">See Also</span></span>  
 [<span data-ttu-id="b5aa0-110">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="b5aa0-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="b5aa0-111">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="b5aa0-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
