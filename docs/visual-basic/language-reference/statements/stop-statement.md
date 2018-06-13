---
title: Stop – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599132"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="0c490-102">Stop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c490-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="0c490-103">Pozastaví spuštění.</span><span class="sxs-lookup"><span data-stu-id="0c490-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c490-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c490-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c490-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c490-105">Remarks</span></span>  
 <span data-ttu-id="0c490-106">Můžete umístit `Stop` příkazy kdekoli v postupech pozastavit provádění.</span><span class="sxs-lookup"><span data-stu-id="0c490-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="0c490-107">Pomocí `Stop` příkaz je podobná nastavením zarážky v kódu.</span><span class="sxs-lookup"><span data-stu-id="0c490-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="0c490-108">`Stop` Příkaz pozastaví spuštění, ale na rozdíl od `End`, nemá zavřete všechny soubory, nebo zrušte všechny proměnné, pokud se vyskytuje v kompilovaném spustitelný soubor (.exe) soubor.</span><span class="sxs-lookup"><span data-stu-id="0c490-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c490-109">Pokud `Stop` je příkaz zjistil v kódu, který je spuštěn mimo integrované vývojové prostředí (IDE), je vyvolána ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0c490-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="0c490-110">To platí bez ohledu na to, jestli se v režimu ladění nebo prodejní zkompilovat kód.</span><span class="sxs-lookup"><span data-stu-id="0c490-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c490-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c490-111">Example</span></span>  
 <span data-ttu-id="0c490-112">Tento příklad používá `Stop` příkaz pozastavit provádění pro každou iteraci prostřednictvím `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="0c490-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0c490-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c490-113">See Also</span></span>  
 [<span data-ttu-id="0c490-114">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="0c490-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
