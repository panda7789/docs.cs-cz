---
title: 'Postupy: Přerušení a kombinování příkazů v kódu (Visual Basic)'
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
ms.openlocfilehash: a0a77b161d81271a4cb7eecf2982a287debee6a5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991728"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="5faf5-102">Postupy: Přerušení a kombinování příkazů v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faf5-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="5faf5-103">Při psaní kódu můžete občas vytvořit zdlouhavé příkazy, které vyžadují horizontální posouvání v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="5faf5-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="5faf5-104">I když to nemá vliv na způsob, jakým se váš kód spouští, ztěžuje vám nebo někomu jinému čtení kódu, jak se zobrazuje na monitoru.</span><span class="sxs-lookup"><span data-stu-id="5faf5-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="5faf5-105">V takových případech byste měli zvážit rozdělení jednoho dlouhého příkazu na několik řádků.</span><span class="sxs-lookup"><span data-stu-id="5faf5-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="5faf5-106">Přerušení jednoho příkazu na více řádků</span><span class="sxs-lookup"><span data-stu-id="5faf5-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="5faf5-107">Použijte znak pro pokračování řádku, což je podtržítko (`_`), v místě, kde má být řádek přerušen.</span><span class="sxs-lookup"><span data-stu-id="5faf5-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="5faf5-108">Podtržítko musí bezprostředně předcházet mezerou a ihned po něm následovat ukončovací znak (návrat vozíku) nebo (počínaje verzí 16,0) komentář následovaný návratem na začátek řádku.</span><span class="sxs-lookup"><span data-stu-id="5faf5-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5faf5-109">V některých případech, Pokud vynecháte znak pro pokračování řádku, kompilátor Visual Basic implicitně pokračuje v příkazu na dalším řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="5faf5-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="5faf5-110">Seznam elementů syntaxe, pro které můžete vynechat znak pro pokračování řádku, naleznete v tématu "implicitní pokračování řádku" v [prohlášeních](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="5faf5-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="5faf5-111">V následujícím příkladu je příkaz rozdělen na čtyři řádky se znaky pro pokračování řádku, které končí všechny kromě posledního řádku.</span><span class="sxs-lookup"><span data-stu-id="5faf5-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="5faf5-112">Použití této sekvence usnadňuje čtení kódu, jak online, tak i po vytištění.</span><span class="sxs-lookup"><span data-stu-id="5faf5-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="5faf5-113">Znak pro pokračování řádku musí být poslední znak na řádku.</span><span class="sxs-lookup"><span data-stu-id="5faf5-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="5faf5-114">Na stejném řádku nemůžete postupovat s jakýmkoli jiným.</span><span class="sxs-lookup"><span data-stu-id="5faf5-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="5faf5-115">Některá omezení existují, jako na to, kde můžete použít znak pro pokračování řádku; Nemůžete ho například použít uprostřed názvu argumentu.</span><span class="sxs-lookup"><span data-stu-id="5faf5-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="5faf5-116">Seznam argumentů lze přerušit pomocí znaku pro pokračování řádku, ale jednotlivé názvy argumentů musí zůstat beze změny.</span><span class="sxs-lookup"><span data-stu-id="5faf5-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="5faf5-117">Komentář nelze pokračovat pomocí znaku pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="5faf5-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="5faf5-118">Kompilátor neověřuje znaky v komentáři pro zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="5faf5-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="5faf5-119">V případě víceřádkového komentáře opakujte symbol komentáře (`'`) na každém řádku.</span><span class="sxs-lookup"><span data-stu-id="5faf5-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="5faf5-120">I když je umístění každého příkazu na samostatném řádku doporučený způsob, Visual Basic také umožňuje umístit více příkazů na stejný řádek.</span><span class="sxs-lookup"><span data-stu-id="5faf5-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="5faf5-121">Postup umístění více příkazů na stejný řádek</span><span class="sxs-lookup"><span data-stu-id="5faf5-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="5faf5-122">Příkazy oddělte dvojtečkou (`:`), jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5faf5-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="5faf5-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5faf5-123">See also</span></span>

- [<span data-ttu-id="5faf5-124">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="5faf5-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="5faf5-125">Příkazy</span><span class="sxs-lookup"><span data-stu-id="5faf5-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
