---
title: Třída delegáta '<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321299"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="5a070-102">Třída delegáta\<classname >' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody</span><span class="sxs-lookup"><span data-stu-id="5a070-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="5a070-103">Volání `Invoke` prostřednictvím delegáta se nezdařila, protože `Invoke` není implementované u třídy delegáta.</span><span class="sxs-lookup"><span data-stu-id="5a070-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="5a070-104">**ID chyby:** BC30220</span><span class="sxs-lookup"><span data-stu-id="5a070-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5a070-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5a070-105">To correct this error</span></span>  
  
1. <span data-ttu-id="5a070-106">Ujistěte se, že byla vytvořena instance třídy delegáta s `Dim` příkazu a, postup byl přiřazen k instanci delegáta s `AddressOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="5a070-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="5a070-107">Vyhledejte kód, který implementuje třídu delegáta a ujistěte se, že implementuje `Invoke` postup.</span><span class="sxs-lookup"><span data-stu-id="5a070-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a070-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a070-108">See also</span></span>

- [<span data-ttu-id="5a070-109">Delegáty</span><span class="sxs-lookup"><span data-stu-id="5a070-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="5a070-110">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a070-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="5a070-111">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="5a070-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="5a070-112">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a070-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
