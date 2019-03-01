---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 3b1a66ecfd3c023a12ac62191ca3671a195b45a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978225"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="60fe6-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60fe6-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="60fe6-103">Označuje, že externí procedura má jiný název ve své DLL.</span><span class="sxs-lookup"><span data-stu-id="60fe6-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60fe6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60fe6-104">Remarks</span></span>  
 <span data-ttu-id="60fe6-105">`Alias` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="60fe6-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="60fe6-106">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="60fe6-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="60fe6-107">V následujícím příkladu `Alias` – klíčové slovo se používá k poskytnutí názvu funkce v advapi32.dll, `GetUserNameA`, který `getUserName` je použito místo v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="60fe6-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="60fe6-108">Funkce `getUserName` je volána v dílčí `getUser`, která zobrazí jméno aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="60fe6-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="60fe6-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60fe6-109">See also</span></span>
- [<span data-ttu-id="60fe6-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="60fe6-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
