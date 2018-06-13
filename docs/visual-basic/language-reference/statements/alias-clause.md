---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 62b34f5860b35104b6a8caa82c359383999dd61b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599171"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="7400a-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7400a-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="7400a-103">Určuje, že externí procedura má jiný název v jeho knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="7400a-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7400a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7400a-104">Remarks</span></span>  
 <span data-ttu-id="7400a-105">`Alias` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="7400a-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="7400a-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="7400a-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="7400a-107">V následujícím příkladu `Alias` – klíčové slovo slouží k zadání názvu funkce v advapi32.dll, `GetUserNameA`, že `getUserName` se v tomto příkladu používá místě.</span><span class="sxs-lookup"><span data-stu-id="7400a-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="7400a-108">Funkce `getUserName` je volána v dílčí `getUser`, který zobrazí název aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="7400a-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7400a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7400a-109">See Also</span></span>  
 [<span data-ttu-id="7400a-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7400a-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
