---
title: Speciální znaky v kódu (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967978"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="c8952-102">Speciální znaky v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8952-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="c8952-103">Někdy je nutné použít speciální znaky v kódu, to znamená, znaky, které nejsou čísla.</span><span class="sxs-lookup"><span data-stu-id="c8952-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="c8952-104">Interpunkce a speciální znaky znakové sady Visual Basic mají různé možnosti použití, z uspořádání textu programu k definování úkolů, které kompilátor nebo zkompilovaný program provede.</span><span class="sxs-lookup"><span data-stu-id="c8952-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="c8952-105">Nezadávejte operaci, která se má provést.</span><span class="sxs-lookup"><span data-stu-id="c8952-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="c8952-106">Závorky</span><span class="sxs-lookup"><span data-stu-id="c8952-106">Parentheses</span></span>  
 <span data-ttu-id="c8952-107">Používejte závorky definuje proceduru, třeba `Sub` nebo `Function`.</span><span class="sxs-lookup"><span data-stu-id="c8952-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="c8952-108">Všechny seznamy argumentů postupu je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="c8952-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="c8952-109">Také při použití závorek k uvedení proměnných nebo argumentů do logických skupin, zejména pro přepsání výchozí pořadí podle priority operátoru ve výrazu komplexní.</span><span class="sxs-lookup"><span data-stu-id="c8952-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="c8952-110">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c8952-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c8952-111">Po spuštění předchozího kódu, hodnota `d` je 8.225 a hodnota `e` je 3.</span><span class="sxs-lookup"><span data-stu-id="c8952-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="c8952-112">Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="c8952-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="c8952-113">Závorky ve výpočtu pro `e` změnit výchozí prioritu.</span><span class="sxs-lookup"><span data-stu-id="c8952-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="c8952-114">Oddělovače</span><span class="sxs-lookup"><span data-stu-id="c8952-114">Separators</span></span>  
 <span data-ttu-id="c8952-115">Oddělovače udělat, co jejich název napovídá: oddělují části kódu.</span><span class="sxs-lookup"><span data-stu-id="c8952-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="c8952-116">V jazyce Visual Basic je oddělovací znak dvojtečky (`:`).</span><span class="sxs-lookup"><span data-stu-id="c8952-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="c8952-117">Používejte oddělovače, při které chcete zahrnout více příkazů na jednom řádku namísto samostatné řádky.</span><span class="sxs-lookup"><span data-stu-id="c8952-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="c8952-118">To šetří místo a zlepšuje čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="c8952-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="c8952-119">Následující příklad ukazuje tři příkazy, které jsou odděleny dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="c8952-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="c8952-120">Další informace najdete v tématu [jak: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="c8952-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="c8952-121">Dvojtečka (`:`) znaků se také používá k identifikaci popisek příkazu.</span><span class="sxs-lookup"><span data-stu-id="c8952-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="c8952-122">Další informace najdete v tématu [jak: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="c8952-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="c8952-123">Zřetězení</span><span class="sxs-lookup"><span data-stu-id="c8952-123">Concatenation</span></span>  
 <span data-ttu-id="c8952-124">Použití `&` operátor pro *zřetězení*, nebo propojení řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8952-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="c8952-125">Nepleťte si jej `+` operátor, který přidá společně číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c8952-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="c8952-126">Pokud používáte `+` operátor zřetězení při pracovat na číselné hodnoty, můžete získat nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="c8952-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="c8952-127">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="c8952-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="c8952-128">Po spuštění předchozího kódu, hodnota `resultA` 21.01 a hodnota `resultB` je "10.0111".</span><span class="sxs-lookup"><span data-stu-id="c8952-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="c8952-129">Operátory přístupu členů</span><span class="sxs-lookup"><span data-stu-id="c8952-129">Member Access Operators</span></span>  
 <span data-ttu-id="c8952-130">Chcete-li přístup ke členu typu, použijte tečku (`.`) nebo vykřičník (`!`) – operátor mezi název typu a název člena.</span><span class="sxs-lookup"><span data-stu-id="c8952-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="c8952-131">Tečka (.) Operátor</span><span class="sxs-lookup"><span data-stu-id="c8952-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="c8952-132">Použití `.` operátor na třídu, strukturu, rozhraní nebo výčet jako operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="c8952-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="c8952-133">Člen může být pole, vlastnosti, události nebo metody.</span><span class="sxs-lookup"><span data-stu-id="c8952-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="c8952-134">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c8952-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="c8952-135">Vykřičník (!) Operátor</span><span class="sxs-lookup"><span data-stu-id="c8952-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="c8952-136">Použití `!` operátor pouze pro třídu nebo rozhraní jako slovník – operátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="c8952-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="c8952-137">Třída nebo rozhraní musí mít výchozí vlastnost, která přijímá jeden `String` argument.</span><span class="sxs-lookup"><span data-stu-id="c8952-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="c8952-138">Identifikátor hned za `!` operátor stane hodnota argumentu předaného výchozí vlastnosti jako řetězec proměnné.</span><span class="sxs-lookup"><span data-stu-id="c8952-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="c8952-139">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="c8952-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c8952-140">Tři výstupní řádky `MsgBox` všechny zobrazit hodnotu `32856`.</span><span class="sxs-lookup"><span data-stu-id="c8952-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="c8952-141">První řádek využívá tradiční přístup k vlastnosti `index`, druhý používá faktu, který `index` je výchozí vlastnost třídy `hasDefault`, a třetí použije slovníkový přístup ke třídě.</span><span class="sxs-lookup"><span data-stu-id="c8952-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="c8952-142">Všimněte si, že druhý operand `!` operator musí být platným identifikátorem jazyka Visual Basic není uzavřen do dvojitých uvozovek (`" "`).</span><span class="sxs-lookup"><span data-stu-id="c8952-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="c8952-143">Jinými slovy nelze použít textový literál nebo proměnná řetězce.</span><span class="sxs-lookup"><span data-stu-id="c8952-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="c8952-144">Následující změnit na poslední řádek `MsgBox` volání dojde k chybě, protože `"X"` je uzavřené řetězec literálu.</span><span class="sxs-lookup"><span data-stu-id="c8952-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="c8952-145">Odkazy na výchozích kolekcí musí být explicitní.</span><span class="sxs-lookup"><span data-stu-id="c8952-145">References to default collections must be explicit.</span></span> <span data-ttu-id="c8952-146">Zejména, nelze použít `!` operátor u proměnné s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="c8952-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="c8952-147">`!` Znak slouží také jako `Single` znak.</span><span class="sxs-lookup"><span data-stu-id="c8952-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8952-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8952-148">See also</span></span>

- [<span data-ttu-id="c8952-149">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="c8952-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="c8952-150">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="c8952-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
