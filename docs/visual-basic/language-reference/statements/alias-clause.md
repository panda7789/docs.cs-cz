---
title: Alias – klauzule (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="de35c-102">Alias – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de35c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="de35c-103">Určuje, že externí procedura má jiný název v jeho knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="de35c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de35c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de35c-104">Remarks</span></span>  
 <span data-ttu-id="de35c-105">`Alias` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="de35c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="de35c-106">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="de35c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="de35c-107">V následujícím příkladu `Alias` – klíčové slovo slouží k zadání názvu funkce v advapi32.dll, `GetUserNameA`, že `getUserName` se v tomto příkladu používá místě.</span><span class="sxs-lookup"><span data-stu-id="de35c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="de35c-108">Funkce `getUserName` je volána v dílčí `getUser`, který zobrazí název aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="de35c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="de35c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="de35c-109">See Also</span></span>  
 [<span data-ttu-id="de35c-110">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="de35c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
