---
title: Operandem 'AddressOf' musí být název metody (bez závorek).
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262111"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="7e40e-102">Operandem 'AddressOf' musí být název metody (bez závorek).</span><span class="sxs-lookup"><span data-stu-id="7e40e-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="7e40e-103">`AddressOf` Operátor vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup.</span><span class="sxs-lookup"><span data-stu-id="7e40e-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="7e40e-104">Syntaxe je následující.</span><span class="sxs-lookup"><span data-stu-id="7e40e-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="7e40e-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="7e40e-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="7e40e-106">Vložení závorek okolo následující argument `AddressOf`, ve kterém není potřeba.</span><span class="sxs-lookup"><span data-stu-id="7e40e-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="7e40e-107">**ID chyby:** BC30577</span><span class="sxs-lookup"><span data-stu-id="7e40e-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e40e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7e40e-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7e40e-109">Odebrat závorky kolem následující argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="7e40e-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="7e40e-110">Ujistěte se, že argument je název metody.</span><span class="sxs-lookup"><span data-stu-id="7e40e-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e40e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e40e-111">See also</span></span>
- [<span data-ttu-id="7e40e-112">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="7e40e-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="7e40e-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="7e40e-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
