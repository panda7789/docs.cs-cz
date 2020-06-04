---
title: Alias – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408468"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="01ac1-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ac1-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="01ac1-103">Označuje, že externí procedura má jiný název ve své knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="01ac1-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ac1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01ac1-104">Remarks</span></span>  
 <span data-ttu-id="01ac1-105">`Alias`Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="01ac1-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="01ac1-106">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="01ac1-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="01ac1-107">V následujícím příkladu se `Alias` klíčové slovo používá k poskytnutí názvu funkce v advapi32. dll, `GetUserNameA` která `getUserName` je použita místo v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="01ac1-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="01ac1-108">Funkce `getUserName` je volána v sub `getUser` , která zobrazuje název aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="01ac1-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="01ac1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="01ac1-109">See also</span></span>

- [<span data-ttu-id="01ac1-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="01ac1-110">Keywords</span></span>](../keywords/index.md)
