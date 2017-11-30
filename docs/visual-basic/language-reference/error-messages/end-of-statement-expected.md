---
title: "Byl očekáván konec příkazu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords: BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="9a36f-102">Byl očekáván konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="9a36f-102">End of statement expected</span></span>
<span data-ttu-id="9a36f-103">Příkaz je syntakticky dokončení, ale další programovací element odpovídá elementu, který dokončí příkaz.</span><span class="sxs-lookup"><span data-stu-id="9a36f-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="9a36f-104">Na konci každé příkaz vyžádáním ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="9a36f-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="9a36f-105">Ukončení řádku rozděluje znaky jazyka Visual Basic zdrojového souboru do řádky.</span><span class="sxs-lookup"><span data-stu-id="9a36f-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="9a36f-106">Příkladem konců řádku jsou kódování Unicode znaků CR návratový znak (& HD) kódování Unicode konce řádku znak (& HA), a znak Unicode vrátí znak, za nímž následuje znak Unicode konce řádku.</span><span class="sxs-lookup"><span data-stu-id="9a36f-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="9a36f-107">Další informace o konců řádku najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a36f-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="9a36f-108">**ID chyby:** BC30205</span><span class="sxs-lookup"><span data-stu-id="9a36f-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a36f-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9a36f-109">To correct this error</span></span>
  
1.  <span data-ttu-id="9a36f-110">Zkontrolujte, pokud dva různé příkazy nechtěně byly uvedeny na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="9a36f-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="9a36f-111">Po elementu, který dokončí příkaz INSERT a ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="9a36f-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9a36f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a36f-112">See Also</span></span>  
 [<span data-ttu-id="9a36f-113">Postupy: přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="9a36f-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="9a36f-114">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9a36f-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
