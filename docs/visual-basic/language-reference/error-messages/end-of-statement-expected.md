---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: ab6a4a0e6736e2af9c1fa0dd170b6aa4c42d9e4a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817147"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="0e630-102">Byl očekáván konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="0e630-102">End of statement expected</span></span>
<span data-ttu-id="0e630-103">Příkaz je syntakticky úplný, ale další programovací element dodržovat elementu, který příkaz se dokončí.</span><span class="sxs-lookup"><span data-stu-id="0e630-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="0e630-104">Vyžaduje na konci každý příkaz se znakem ukončení řádku.</span><span class="sxs-lookup"><span data-stu-id="0e630-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="0e630-105">Ukončení řádku rozdělí řádky znaků zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0e630-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="0e630-106">Příkladem řádku jsou kódování Unicode návrat na začátek řádku návratový znak (& HD, High Density), Unicode odřádkování znak (& HA), a Unicode návrat znak následovaný znak odřádkování Unicode.</span><span class="sxs-lookup"><span data-stu-id="0e630-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="0e630-107">Další informace o řádku, najdete v článku [specifikace jazyka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="0e630-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="0e630-108">**ID chyby:** BC30205</span><span class="sxs-lookup"><span data-stu-id="0e630-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e630-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0e630-109">To correct this error</span></span>
  
1.  <span data-ttu-id="0e630-110">Zaškrtněte, pokud chcete zobrazit, pokud dva různé příkazy neúmyslně byly uvedeny na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="0e630-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="0e630-111">Vložte a znak ukončení řádku za prvkem, který se příkaz dokončí.</span><span class="sxs-lookup"><span data-stu-id="0e630-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e630-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e630-112">See also</span></span>

- [<span data-ttu-id="0e630-113">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="0e630-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="0e630-114">Příkazy</span><span class="sxs-lookup"><span data-stu-id="0e630-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
