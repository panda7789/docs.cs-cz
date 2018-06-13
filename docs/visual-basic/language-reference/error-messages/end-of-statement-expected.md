---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588077"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="25d36-102">Byl očekáván konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="25d36-102">End of statement expected</span></span>
<span data-ttu-id="25d36-103">Příkaz je syntakticky dokončení, ale další programovací element odpovídá elementu, který dokončí příkaz.</span><span class="sxs-lookup"><span data-stu-id="25d36-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="25d36-104">Na konci každé příkaz vyžádáním ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="25d36-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="25d36-105">Ukončení řádku rozděluje znaky jazyka Visual Basic zdrojového souboru do řádky.</span><span class="sxs-lookup"><span data-stu-id="25d36-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="25d36-106">Příkladem konců řádku jsou kódování Unicode znaků CR návratový znak (& HD) kódování Unicode konce řádku znak (& HA), a znak Unicode vrátí znak, za nímž následuje znak Unicode konce řádku.</span><span class="sxs-lookup"><span data-stu-id="25d36-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="25d36-107">Další informace o konců řádku najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="25d36-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="25d36-108">**ID chyby:** BC30205</span><span class="sxs-lookup"><span data-stu-id="25d36-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25d36-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="25d36-109">To correct this error</span></span>
  
1.  <span data-ttu-id="25d36-110">Zkontrolujte, pokud dva různé příkazy nechtěně byly uvedeny na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="25d36-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="25d36-111">Po elementu, který dokončí příkaz INSERT a ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="25d36-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="25d36-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="25d36-112">See Also</span></span>  
 [<span data-ttu-id="25d36-113">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="25d36-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="25d36-114">Příkazy</span><span class="sxs-lookup"><span data-stu-id="25d36-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
