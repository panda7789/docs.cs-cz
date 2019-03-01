---
title: 'Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: a43d09be53eb5a04d154e482f9388e2ca480118a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967175"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="68dbf-102">Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68dbf-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="68dbf-103">Při psaní kódu, může být čas od času vytvoření dlouhé příkazy, které vyžadují vodorovného posouvání v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="68dbf-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="68dbf-104">I když to nemá vliv způsob, jak kód poběží, to ztěžuje pro vás nebo někdo jiný kód přečíst, jak je zobrazen na monitorování.</span><span class="sxs-lookup"><span data-stu-id="68dbf-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="68dbf-105">V takovém případě zvažte rozdělení jeden dlouhý příkaz na několika řádcích.</span><span class="sxs-lookup"><span data-stu-id="68dbf-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="68dbf-106">Chcete rozdělit jeden příkaz na více řádků</span><span class="sxs-lookup"><span data-stu-id="68dbf-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="68dbf-107">Použijte znak pro pokračování řádku, který je podtržítko (`_`), v okamžiku, kdy chcete řádek rozdělit.</span><span class="sxs-lookup"><span data-stu-id="68dbf-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="68dbf-108">Podtržítka musí být bezprostředně předchází mezerou a ihned následovány znakem ukončení řádku (návrat).</span><span class="sxs-lookup"><span data-stu-id="68dbf-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="68dbf-109">V některých případech Pokud vynecháte znak pro pokračování řádku, kompilátor jazyka Visual Basic implicitně bude příkaz na další řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="68dbf-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="68dbf-110">Seznam prvky syntaxe, pro které je možné vynechat znak pro pokračování řádku naleznete v části "Implicitní pokračování řádku" v [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="68dbf-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="68dbf-111">V následujícím příkladu příkaz rozdělená do čtyř řádků se ukončuje všechny znaky pokračování řádku, ale na posledním řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     <span data-ttu-id="68dbf-112">Pomocí tohoto pořadí díky váš kód lépe čitelný, online i při tisku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="68dbf-113">Znak pokračování řádku musí být poslední znak na řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="68dbf-114">Ho nemůže následovat s cokoli na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="68dbf-115">Existují určitá omezení, kde můžete použít znak pokračování řádku. například nelze použít uprostřed název argumentu.</span><span class="sxs-lookup"><span data-stu-id="68dbf-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="68dbf-116">Můžete přerušit seznam argumentů znakem pokračování řádku, ale jednotlivé názvy argumentů, musí zůstat beze změny.</span><span class="sxs-lookup"><span data-stu-id="68dbf-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="68dbf-117">Komentář nemůže pokračovat s použitím znak pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="68dbf-118">Kompilátor nebude zkontrolujte znaky v komentáři pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="68dbf-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="68dbf-119">Více řádků komentáře, opakujte symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="68dbf-120">I když každý příkaz umístit na samostatný řádek je doporučená metoda, Visual Basic také umožňuje umístit více příkazů na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="68dbf-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="68dbf-121">Umístit více příkazů na stejném řádku</span><span class="sxs-lookup"><span data-stu-id="68dbf-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="68dbf-122">Oddělení příkazů s dvojtečkou (`:`), jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="68dbf-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="68dbf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68dbf-123">See also</span></span>
- [<span data-ttu-id="68dbf-124">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="68dbf-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="68dbf-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="68dbf-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
