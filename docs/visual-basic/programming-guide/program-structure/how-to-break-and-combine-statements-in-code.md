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
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651015"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="c8d34-102">Postupy: Přerušení a kombinace příkazů v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d34-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="c8d34-103">Při psaní kódu, můžete vytvořit v některých případech zdlouhavé příkazy, které vyžadují vodorovného posouvání v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="c8d34-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="c8d34-104">I když to nemá vliv způsob kód běží, je ztížíte pro vy ani nikdo jiný číst kód, jak se objevuje v monitorování.</span><span class="sxs-lookup"><span data-stu-id="c8d34-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="c8d34-105">V takovém případě byste měli zvážit, rozdělení jeden dlouhý příkaz na několika řádcích.</span><span class="sxs-lookup"><span data-stu-id="c8d34-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="c8d34-106">Chcete-li rozdělit jeden příkaz na více řádků</span><span class="sxs-lookup"><span data-stu-id="c8d34-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="c8d34-107">Použít znak pokračování řádku, který je podtržítko (`_`), v okamžiku, kdy chcete řádek ukončit.</span><span class="sxs-lookup"><span data-stu-id="c8d34-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="c8d34-108">Podtržítko musí být bezprostředně před mezerou a bezprostředně následované ukončení řádku (návrat na začátek).</span><span class="sxs-lookup"><span data-stu-id="c8d34-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8d34-109">V některých případech Pokud vynecháte znak pokračování řádku Visual Basic – kompilátor implicitně bude příkaz na dalším řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="c8d34-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="c8d34-110">Seznam prvků syntaxe, pro které je možné vynechat znak pokračování řádku najdete v tématu "Implicitní pokračování řádku" v [příkazy](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="c8d34-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="c8d34-111">V následujícím příkladu je příkaz rozdělená do čtyř řádky s znaky pokračování řádku ukončení všech ale poslední řádek.</span><span class="sxs-lookup"><span data-stu-id="c8d34-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     <span data-ttu-id="c8d34-112">Pomocí tohoto pořadí usnadňuje kódu čtení, online i když vytisknout.</span><span class="sxs-lookup"><span data-stu-id="c8d34-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="c8d34-113">Znak pokračování řádku musí být poslední znak na řádek.</span><span class="sxs-lookup"><span data-stu-id="c8d34-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="c8d34-114">Nelze ho sledovat s cokoliv jiného na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="c8d34-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="c8d34-115">Existují některá omezení, kde můžete použít znak pokračování řádku; například nelze použít uprostřed název argumentu.</span><span class="sxs-lookup"><span data-stu-id="c8d34-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="c8d34-116">Seznam argumentů s znak pokračování řádku je možné přerušit, ale jednotlivé názvy argumenty, které musí zůstat beze změn.</span><span class="sxs-lookup"><span data-stu-id="c8d34-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="c8d34-117">Komentář nemůže pokračovat s použitím znak pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="c8d34-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="c8d34-118">Kompilátor není zkontrolujte znaků v komentáři pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="c8d34-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="c8d34-119">Pro více řádků komentář, opakujte symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="c8d34-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="c8d34-120">I když každý příkaz umístění na samostatném řádku je doporučená metoda, Visual Basic také umožňuje umístit více příkazů na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="c8d34-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="c8d34-121">Umístit více příkazů na stejné přímce.</span><span class="sxs-lookup"><span data-stu-id="c8d34-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="c8d34-122">Příkazy oddělte čárkou (`:`), jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c8d34-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c8d34-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8d34-123">See Also</span></span>  
 [<span data-ttu-id="c8d34-124">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="c8d34-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="c8d34-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="c8d34-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
