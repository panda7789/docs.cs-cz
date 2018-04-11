---
title: '& č. 39; AddressOf & č. 39; operand musí být název metody (bez závorek).'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="07b85-102">& č. 39; AddressOf & č. 39; operand musí být název metody (bez závorek).</span><span class="sxs-lookup"><span data-stu-id="07b85-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="07b85-103">`AddressOf` Operátor vytvoří instanci postup delegáta, který odkazuje na zvláštní postup.</span><span class="sxs-lookup"><span data-stu-id="07b85-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="07b85-104">Syntaxe je následující.</span><span class="sxs-lookup"><span data-stu-id="07b85-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="07b85-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="07b85-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="07b85-106">Vložit v závorkách následující argument `AddressOf`, kde není potřeba.</span><span class="sxs-lookup"><span data-stu-id="07b85-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="07b85-107">**ID chyby:** BC30577</span><span class="sxs-lookup"><span data-stu-id="07b85-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07b85-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="07b85-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="07b85-109">Odebrat závorkách následující argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="07b85-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="07b85-110">Zkontrolujte, zda že je název metody.</span><span class="sxs-lookup"><span data-stu-id="07b85-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b85-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="07b85-111">See Also</span></span>  
 [<span data-ttu-id="07b85-112">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="07b85-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="07b85-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="07b85-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
