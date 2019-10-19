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
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583222"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="e8b72-102">Stop – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8b72-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="e8b72-103">Pozastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="e8b72-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8b72-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8b72-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8b72-105">Remarks</span></span>  
 <span data-ttu-id="e8b72-106">Můžete umístit `Stop` příkazy kdekoli v postupech pro pozastavení provádění.</span><span class="sxs-lookup"><span data-stu-id="e8b72-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="e8b72-107">Použití příkazu `Stop` je podobné jako nastavení zarážky v kódu.</span><span class="sxs-lookup"><span data-stu-id="e8b72-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="e8b72-108">Příkaz `Stop` pozastaví provádění, ale na rozdíl od `End` nezavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).</span><span class="sxs-lookup"><span data-stu-id="e8b72-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b72-109">Pokud je v kódu, který běží mimo integrované vývojové prostředí (IDE), nalezen příkaz `Stop`, je vyvolán ladicí program.</span><span class="sxs-lookup"><span data-stu-id="e8b72-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="e8b72-110">To platí bez ohledu na to, zda byl kód zkompilován v režimu ladění nebo maloobchodu.</span><span class="sxs-lookup"><span data-stu-id="e8b72-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b72-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8b72-111">Example</span></span>  
 <span data-ttu-id="e8b72-112">V tomto příkladu se používá příkaz `Stop` k pozastavení provádění každé iterace prostřednictvím smyčky `For...Next`.</span><span class="sxs-lookup"><span data-stu-id="e8b72-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="e8b72-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8b72-113">See also</span></span>

- [<span data-ttu-id="e8b72-114">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="e8b72-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
