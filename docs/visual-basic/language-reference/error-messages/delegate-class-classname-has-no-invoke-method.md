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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321299"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="2eb12-102">Třída delegáta\<classname >' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody</span><span class="sxs-lookup"><span data-stu-id="2eb12-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="2eb12-103">Volání `Invoke` prostřednictvím delegáta se nezdařila, protože `Invoke` není implementované u třídy delegáta.</span><span class="sxs-lookup"><span data-stu-id="2eb12-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="2eb12-104">**ID chyby:** BC30220</span><span class="sxs-lookup"><span data-stu-id="2eb12-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2eb12-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2eb12-105">To correct this error</span></span>  
  
1. <span data-ttu-id="2eb12-106">Ujistěte se, že byla vytvořena instance třídy delegáta s `Dim` příkazu a, postup byl přiřazen k instanci delegáta s `AddressOf` operátor.</span><span class="sxs-lookup"><span data-stu-id="2eb12-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="2eb12-107">Vyhledejte kód, který implementuje třídu delegáta a ujistěte se, že implementuje `Invoke` postup.</span><span class="sxs-lookup"><span data-stu-id="2eb12-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb12-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eb12-108">See also</span></span>

- [<span data-ttu-id="2eb12-109">Delegáti</span><span class="sxs-lookup"><span data-stu-id="2eb12-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="2eb12-110">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="2eb12-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="2eb12-111">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="2eb12-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2eb12-112">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="2eb12-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
