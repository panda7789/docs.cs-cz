---
title: Delegovat třída &#39; &lt;classname&gt; &#39; má metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588827"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="8ae2e-102">Delegovat třída &#39; &lt;classname&gt; &#39; má metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody</span><span class="sxs-lookup"><span data-stu-id="8ae2e-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="8ae2e-103">Volání `Invoke` prostřednictvím delegáta se nezdařil, protože `Invoke` není implementována ve třídě delegáta.</span><span class="sxs-lookup"><span data-stu-id="8ae2e-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="8ae2e-104">**ID chyby:** BC30220</span><span class="sxs-lookup"><span data-stu-id="8ae2e-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ae2e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8ae2e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="8ae2e-106">Ujistěte se, že instance třídy delegáta byl vytvořen s `Dim` prohlášení a zda procedury byla přiřazena instance delegáta s `AddressOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="8ae2e-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="8ae2e-107">Vyhledejte kód, který implementuje třídu delegáta a zajistěte, aby se implementuje `Invoke` postupu.</span><span class="sxs-lookup"><span data-stu-id="8ae2e-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae2e-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ae2e-108">See Also</span></span>  
 [<span data-ttu-id="8ae2e-109">Delegáti</span><span class="sxs-lookup"><span data-stu-id="8ae2e-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="8ae2e-110">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="8ae2e-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="8ae2e-111">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="8ae2e-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="8ae2e-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="8ae2e-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
