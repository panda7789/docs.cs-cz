---
title: "Speciální znaky v kódu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11c5ef9ad41fc2362d9ba4f2cb5eb5b63a9ca31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="e8e9f-102">Speciální znaky v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e9f-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="e8e9f-103">Někdy je nutné použít speciální znaky v kódu, který je znaků, které nejsou abecední nebo číselný.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="e8e9f-104">Interpunkce a speciální znaky v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] znaková sada mají různé používá z uspořádání program text, který má definice úlohy, které provádí kompilátor nebo zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-104">The punctuation and special characters in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="e8e9f-105">Nezadávejte provést operaci.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="e8e9f-106">Závorky</span><span class="sxs-lookup"><span data-stu-id="e8e9f-106">Parentheses</span></span>  
 <span data-ttu-id="e8e9f-107">Závorky lze použít, když definujete postup, například `Sub` nebo `Function`.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="e8e9f-108">Všechny seznamy argumentů postupu je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="e8e9f-109">Také pomocí závorek pro umístění proměnné nebo argumenty do logických skupin, zejména přepsat výchozí pořadí operátorů v složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="e8e9f-110">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 <span data-ttu-id="e8e9f-111">Provedení předchozí kódu hodnotu `d` 8.225 a hodnota `e` je 3.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="e8e9f-112">Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="e8e9f-113">Závorky při výpočtu `e` změnit výchozí prioritu.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="e8e9f-114">Oddělovače</span><span class="sxs-lookup"><span data-stu-id="e8e9f-114">Separators</span></span>  
 <span data-ttu-id="e8e9f-115">Oddělovače udělat, co navrhuje jména: oddělit sekcí kódu.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="e8e9f-116">V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], oddělovací znak je dvojtečkou (`:`).</span><span class="sxs-lookup"><span data-stu-id="e8e9f-116">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="e8e9f-117">Oddělovače použijte, pokud chcete zahrnout více příkazů na jeden řádek místo samostatné řádky.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="e8e9f-118">Tím ušetříte místo a zlepšuje čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="e8e9f-119">Následující příklad ukazuje tři příkazy oddělené dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 <span data-ttu-id="e8e9f-120">Další informace najdete v tématu [postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="e8e9f-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="e8e9f-121">Dvojtečkou (`:`) znak slouží také k identifikaci příkaz štítek.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="e8e9f-122">Další informace najdete v tématu [postup: příkazy popisek](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e9f-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="e8e9f-123">Zřetězení</span><span class="sxs-lookup"><span data-stu-id="e8e9f-123">Concatenation</span></span>  
 <span data-ttu-id="e8e9f-124">Použití `&` operátor pro *zřetězení*, nebo společně propojení řetězce.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="e8e9f-125">Nepleťte si její `+` operátor, který přidá společně číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="e8e9f-126">Pokud použijete `+` operátor ke zřetězení při pracovat na číselné hodnoty, můžete získat nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="e8e9f-127">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 <span data-ttu-id="e8e9f-128">Provedení předchozí kódu hodnotu `resultA` 21.01 a hodnota `resultB` je "10.0111".</span><span class="sxs-lookup"><span data-stu-id="e8e9f-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="e8e9f-129">Operátory pro přístup ke člena</span><span class="sxs-lookup"><span data-stu-id="e8e9f-129">Member Access Operators</span></span>  
 <span data-ttu-id="e8e9f-130">O přístup člena typu, použijte tečky (`.`) nebo vykřičník (`!`) operátor mezi název typu a název člena.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="e8e9f-131">Tečku (.) Operátor</span><span class="sxs-lookup"><span data-stu-id="e8e9f-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="e8e9f-132">Použití `.` operátor na třídy, struktury, rozhraní nebo výčtu jako operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="e8e9f-133">Člen může být pole, vlastnosti, události nebo metody.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="e8e9f-134">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="e8e9f-135">Vykřičník (!) Operátor</span><span class="sxs-lookup"><span data-stu-id="e8e9f-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="e8e9f-136">Použití `!` operátor pouze na třídy nebo rozhraní jako operátor přístupu slovníku.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="e8e9f-137">Třídy nebo rozhraní musí mít výchozí vlastnosti, která přijímá jeden `String` argument.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="e8e9f-138">Identifikátor hned `!` operátor stane hodnota argumentu předaného proměnné výchozí vlastnosti jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="e8e9f-139">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 <span data-ttu-id="e8e9f-140">Jsou tři výstup řádků `MsgBox` všechny zobrazit hodnotu `32856`.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="e8e9f-141">První řádek používá tradiční přístup k vlastnosti `index`, druhý využívá fakt, který `index` je výchozí vlastnost třídy `hasDefault`, a třetí používá slovníkový přístup ke třídě.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="e8e9f-142">Všimněte si, že druhý operand `!` operátor musí být platný identifikátor jazyka Visual Basic není uzavřena v uvozovkách (`" "`).</span><span class="sxs-lookup"><span data-stu-id="e8e9f-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="e8e9f-143">Jinými slovy nemůžete použít řetězcový literál nebo proměnná řetězce.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="e8e9f-144">Následující změnit na poslední řádek `MsgBox` volání vygeneruje chybu, protože `"X"` nachází závorkách řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="e8e9f-145">Odkazy na výchozích kolekcí musí být explicitní.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-145">References to default collections must be explicit.</span></span> <span data-ttu-id="e8e9f-146">Konkrétně nelze použít `!` operátor na proměnnou pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="e8e9f-147">`!` Znak se používá jako `Single` zadávat znaky.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e9f-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8e9f-148">See Also</span></span>  
 [<span data-ttu-id="e8e9f-149">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="e8e9f-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="e8e9f-150">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="e8e9f-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
