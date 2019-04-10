---
title: Operandem 'AddressOf' musí být název metody (bez závorek).
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323821"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="a3eab-102">Operandem 'AddressOf' musí být název metody (bez závorek).</span><span class="sxs-lookup"><span data-stu-id="a3eab-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="a3eab-103">`AddressOf` Operátor vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup.</span><span class="sxs-lookup"><span data-stu-id="a3eab-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="a3eab-104">Syntaxe je následující.</span><span class="sxs-lookup"><span data-stu-id="a3eab-104">The syntax is as follows.</span></span>  
  
 `AddressOf` `procedurename`  
  
 <span data-ttu-id="a3eab-105">Vložení závorek okolo následující argument `AddressOf`, ve kterém není potřeba.</span><span class="sxs-lookup"><span data-stu-id="a3eab-105">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="a3eab-106">**ID chyby:** BC30577</span><span class="sxs-lookup"><span data-stu-id="a3eab-106">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3eab-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a3eab-107">To correct this error</span></span>  
  
1. <span data-ttu-id="a3eab-108">Odebrat závorky kolem následující argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="a3eab-108">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="a3eab-109">Ujistěte se, že argument je název metody.</span><span class="sxs-lookup"><span data-stu-id="a3eab-109">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3eab-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3eab-110">See also</span></span>

- [<span data-ttu-id="a3eab-111">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="a3eab-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="a3eab-112">Delegáty</span><span class="sxs-lookup"><span data-stu-id="a3eab-112">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
