---
title: Třída delegáta '<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 27be97ba2930791bcb9012c824bc418a0089b037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409709"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="58f4a-102">Třída delegáta '\<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.</span><span class="sxs-lookup"><span data-stu-id="58f4a-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="58f4a-103">Volání `Invoke` prostřednictvím delegáta se nezdařilo, protože není `Invoke` implementováno ve třídě Delegate.</span><span class="sxs-lookup"><span data-stu-id="58f4a-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="58f4a-104">**ID chyby:** BC30220</span><span class="sxs-lookup"><span data-stu-id="58f4a-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58f4a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="58f4a-105">To correct this error</span></span>  
  
1. <span data-ttu-id="58f4a-106">Zajistěte, aby byla instance třídy Delegate vytvořená `Dim` příkazem a aby byla procedura přiřazena k instanci delegáta s `AddressOf` operátorem.</span><span class="sxs-lookup"><span data-stu-id="58f4a-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="58f4a-107">Vyhledejte kód, který implementuje třídu delegáta, a ujistěte se, že implementuje `Invoke` proceduru.</span><span class="sxs-lookup"><span data-stu-id="58f4a-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f4a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f4a-108">See also</span></span>

- [<span data-ttu-id="58f4a-109">Delegáti</span><span class="sxs-lookup"><span data-stu-id="58f4a-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="58f4a-110">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="58f4a-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="58f4a-111">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="58f4a-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="58f4a-112">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="58f4a-112">Dim Statement</span></span>](../statements/dim-statement.md)
