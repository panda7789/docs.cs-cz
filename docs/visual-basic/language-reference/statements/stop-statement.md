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
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624779"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="c6ff9-102">Stop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ff9-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="c6ff9-103">Pozastaví provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ff9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ff9-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6ff9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ff9-105">Remarks</span></span>  
 <span data-ttu-id="c6ff9-106">Můžete umístit `Stop` příkazy kdekoli v postupech k pozastavení provádění.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="c6ff9-107">Použití `Stop` příkaz je podobný nastavením zarážky v kódu.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="c6ff9-108">`Stop` Příkaz pozastaví provádění, ale na rozdíl od `End`, ne zavřít všechny soubory, nebo zrušte všechny proměnné, pokud není nalezen v souboru zkompilovaného spustitelného souboru (.exe).</span><span class="sxs-lookup"><span data-stu-id="c6ff9-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6ff9-109">Pokud `Stop` příkaz dochází v kódu, který běží mimo integrované vývojové prostředí (IDE), ladicí program je vyvolán.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="c6ff9-110">To platí bez ohledu na to, zda byl zkompilován kódu v režimu ladění nebo maloobchodního prodeje.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ff9-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6ff9-111">Example</span></span>  
 <span data-ttu-id="c6ff9-112">V tomto příkladu `Stop` příkaz k pozastavení provádění pro každou iteraci přes `For...Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="c6ff9-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6ff9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6ff9-113">See also</span></span>
- [<span data-ttu-id="c6ff9-114">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="c6ff9-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
