---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053350"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="a7f9c-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7f9c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="a7f9c-103">Označuje, že externí procedura má jiný název ve své DLL.</span><span class="sxs-lookup"><span data-stu-id="a7f9c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7f9c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7f9c-104">Remarks</span></span>  
 <span data-ttu-id="a7f9c-105">`Alias` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="a7f9c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="a7f9c-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="a7f9c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="a7f9c-107">V následujícím příkladu `Alias` – klíčové slovo se používá k poskytnutí názvu funkce v advapi32.dll, `GetUserNameA`, který `getUserName` je použito místo v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a7f9c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="a7f9c-108">Funkce `getUserName` je volána v dílčí `getUser`, která zobrazí jméno aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="a7f9c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a7f9c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7f9c-109">See also</span></span>

- [<span data-ttu-id="a7f9c-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a7f9c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
