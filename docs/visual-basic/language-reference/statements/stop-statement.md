---
title: Stop – příkaz
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
ms.openlocfilehash: 2ef1e2f9045e5509e11557c9fdaf3edd2786b72c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404223"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="cd61a-102">Stop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd61a-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="cd61a-103">Pozastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="cd61a-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd61a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd61a-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd61a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd61a-105">Remarks</span></span>  
 <span data-ttu-id="cd61a-106">Příkazy lze umístit `Stop` kdekoli v postupech pro pozastavení provádění.</span><span class="sxs-lookup"><span data-stu-id="cd61a-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="cd61a-107">Použití `Stop` příkazu je podobné jako nastavení zarážky v kódu.</span><span class="sxs-lookup"><span data-stu-id="cd61a-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="cd61a-108">`Stop`Příkaz pozastaví provádění, ale na rozdíl od `End` , neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).</span><span class="sxs-lookup"><span data-stu-id="cd61a-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd61a-109">Je `Stop` -li příkaz nalezen v kódu, který je spuštěn mimo integrované vývojové prostředí (IDE), je vyvolán ladicí program.</span><span class="sxs-lookup"><span data-stu-id="cd61a-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="cd61a-110">To platí bez ohledu na to, zda byl kód zkompilován v režimu ladění nebo maloobchodu.</span><span class="sxs-lookup"><span data-stu-id="cd61a-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd61a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd61a-111">Example</span></span>  
 <span data-ttu-id="cd61a-112">V tomto příkladu se používá `Stop` příkaz pro pozastavení provádění každé iterace prostřednictvím `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="cd61a-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="cd61a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd61a-113">See also</span></span>

- [<span data-ttu-id="cd61a-114">Příkaz end</span><span class="sxs-lookup"><span data-stu-id="cd61a-114">End Statement</span></span>](end-statement.md)
