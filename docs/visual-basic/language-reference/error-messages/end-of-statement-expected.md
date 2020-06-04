---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 169f01b02df377ba6cc21ffad53c36f5d4537140
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409644"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="6dbf6-102">Byl očekáván konec příkazu.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-102">End of statement expected</span></span>
<span data-ttu-id="6dbf6-103">Příkaz je syntakticky dokončen, ale další programovací prvek následuje za prvkem, který dokončí příkaz.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="6dbf6-104">Na konci každého příkazu je vyžadován ukončovací znak řádku.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="6dbf6-105">Zakončení řádku rozděluje znaky zdrojového souboru Visual Basic do řádků.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="6dbf6-106">Příklady zakončení řádků jsou návratový znak Unicode (&HD), znak odřádkování Unicode (&HA) a znak návratu na začátek řádku Unicode následovaný znakem odřádkování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="6dbf6-107">Další informace o ukončovacích koncích řádků najdete v tématu [specifikace jazyka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="6dbf6-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="6dbf6-108">**ID chyby:** BC30205</span><span class="sxs-lookup"><span data-stu-id="6dbf6-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dbf6-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6dbf6-109">To correct this error</span></span>
  
1. <span data-ttu-id="6dbf6-110">Zkontrolujte, zda byly na stejný řádek neúmyslně vloženy dva různé příkazy.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2. <span data-ttu-id="6dbf6-111">Vložte ukončovací znak řádku za prvek, který dokončí příkaz.</span><span class="sxs-lookup"><span data-stu-id="6dbf6-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6dbf6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6dbf6-112">See also</span></span>

- [<span data-ttu-id="6dbf6-113">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="6dbf6-113">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="6dbf6-114">Příkazy</span><span class="sxs-lookup"><span data-stu-id="6dbf6-114">Statements</span></span>](../../programming-guide/language-features/statements.md)
