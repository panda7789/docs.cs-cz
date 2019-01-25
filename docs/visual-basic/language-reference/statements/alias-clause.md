---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 9cf97402d0b0a6cd16dd75a970c1d29a2fcc30a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498567"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="fad4c-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fad4c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="fad4c-103">Označuje, že externí procedura má jiný název ve své DLL.</span><span class="sxs-lookup"><span data-stu-id="fad4c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fad4c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fad4c-104">Remarks</span></span>  
 <span data-ttu-id="fad4c-105">`Alias` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="fad4c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="fad4c-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="fad4c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="fad4c-107">V následujícím příkladu `Alias` – klíčové slovo se používá k poskytnutí názvu funkce v advapi32.dll, `GetUserNameA`, který `getUserName` je použito místo v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="fad4c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="fad4c-108">Funkce `getUserName` je volána v dílčí `getUser`, která zobrazí jméno aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="fad4c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fad4c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fad4c-109">See also</span></span>
- [<span data-ttu-id="fad4c-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fad4c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
