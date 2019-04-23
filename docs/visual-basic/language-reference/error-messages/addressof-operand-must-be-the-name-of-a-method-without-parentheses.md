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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323821"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="0d594-102">Operandem 'AddressOf' musí být název metody (bez závorek).</span><span class="sxs-lookup"><span data-stu-id="0d594-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="0d594-103">`AddressOf` Operátor vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup.</span><span class="sxs-lookup"><span data-stu-id="0d594-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="0d594-104">Syntaxe je následující.</span><span class="sxs-lookup"><span data-stu-id="0d594-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="0d594-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="0d594-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="0d594-106">Vložení závorek okolo následující argument `AddressOf`, ve kterém není potřeba.</span><span class="sxs-lookup"><span data-stu-id="0d594-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="0d594-107">**ID chyby:** BC30577</span><span class="sxs-lookup"><span data-stu-id="0d594-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0d594-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0d594-108">To correct this error</span></span>  
  
1. <span data-ttu-id="0d594-109">Odebrat závorky kolem následující argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="0d594-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="0d594-110">Ujistěte se, že argument je název metody.</span><span class="sxs-lookup"><span data-stu-id="0d594-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d594-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d594-111">See also</span></span>

- [<span data-ttu-id="0d594-112">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="0d594-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="0d594-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="0d594-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
