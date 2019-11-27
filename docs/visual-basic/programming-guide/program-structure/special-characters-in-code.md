---
title: Speciální znaky v kódu
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
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347256"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="165a2-102">Speciální znaky v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="165a2-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="165a2-103">Někdy je nutné použít ve svém kódu speciální znaky, tj. znaky, které nejsou abecední nebo číselné.</span><span class="sxs-lookup"><span data-stu-id="165a2-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="165a2-104">Interpunkční znaménka a speciální znaky ve znakové sadě Visual Basic mají různá použití, od uspořádání textu programu k definování úkolů, které kompilátor nebo zkompilovaný program provádí.</span><span class="sxs-lookup"><span data-stu-id="165a2-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="165a2-105">Neurčují operaci, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="165a2-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="165a2-106">závorky</span><span class="sxs-lookup"><span data-stu-id="165a2-106">Parentheses</span></span>  
 <span data-ttu-id="165a2-107">Při definování procedury, například `Sub` nebo `Function`, použijte závorky.</span><span class="sxs-lookup"><span data-stu-id="165a2-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="165a2-108">Všechny seznamy argumentů procedury musí být uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="165a2-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="165a2-109">Můžete také použít kulaté závorky pro vložení proměnných nebo argumentů do logických skupin, zejména pro přepsání výchozího pořadí priorit operátoru ve složitém výrazu.</span><span class="sxs-lookup"><span data-stu-id="165a2-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="165a2-110">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="165a2-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="165a2-111">Po provedení předchozího kódu je hodnota `d` 8,225 a hodnota `e` je 3.</span><span class="sxs-lookup"><span data-stu-id="165a2-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="165a2-112">Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="165a2-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="165a2-113">Závorky ve výpočtu pro `e` přepisují výchozí prioritu.</span><span class="sxs-lookup"><span data-stu-id="165a2-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="165a2-114">Oddělovače</span><span class="sxs-lookup"><span data-stu-id="165a2-114">Separators</span></span>  
 <span data-ttu-id="165a2-115">Oddělovače podle jejich názvu: oddělují oddíly kódu.</span><span class="sxs-lookup"><span data-stu-id="165a2-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="165a2-116">V Visual Basic je znak oddělovače dvojtečkou (`:`).</span><span class="sxs-lookup"><span data-stu-id="165a2-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="165a2-117">Oddělovače použijte, pokud chcete zahrnout více příkazů na jeden řádek místo samostatných řádků.</span><span class="sxs-lookup"><span data-stu-id="165a2-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="165a2-118">Tím ušetříte místo a zlepšíte čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="165a2-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="165a2-119">Následující příklad ukazuje tři příkazy oddělené dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="165a2-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="165a2-120">Další informace naleznete v tématu [How to: break and kombinovat příkazy v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="165a2-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="165a2-121">Znak dvojtečky (`:`) se používá také k identifikaci popisku příkazu.</span><span class="sxs-lookup"><span data-stu-id="165a2-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="165a2-122">Další informace naleznete v tématu [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="165a2-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="165a2-123">Zřetězení</span><span class="sxs-lookup"><span data-stu-id="165a2-123">Concatenation</span></span>  
 <span data-ttu-id="165a2-124">Použijte operátor `&` pro *zřetězení*nebo propojení řetězců dohromady.</span><span class="sxs-lookup"><span data-stu-id="165a2-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="165a2-125">Nepleťte si ho s operátorem `+`, který přidá dohromady číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="165a2-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="165a2-126">Použijete-li operátor `+` k zřetězení při práci s číselnými hodnotami, můžete získat nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="165a2-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="165a2-127">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="165a2-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="165a2-128">Po provedení předchozího kódu je hodnota `resultA` 21,01 a hodnota `resultB` je "10,0111".</span><span class="sxs-lookup"><span data-stu-id="165a2-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="165a2-129">Operátory přístupu členů</span><span class="sxs-lookup"><span data-stu-id="165a2-129">Member Access Operators</span></span>  
 <span data-ttu-id="165a2-130">Chcete-li získat přístup ke členu typu, použijte operátor tečka (`.`) nebo vykřičník (`!`) mezi názvem typu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="165a2-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="165a2-131">Tečka (.) Podnikatel</span><span class="sxs-lookup"><span data-stu-id="165a2-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="165a2-132">Použijte operátor `.` pro třídu, strukturu, rozhraní nebo výčet jako operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="165a2-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="165a2-133">Členem může být pole, vlastnost, událost nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="165a2-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="165a2-134">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="165a2-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="165a2-135">Vykřičník (!) Podnikatel</span><span class="sxs-lookup"><span data-stu-id="165a2-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="165a2-136">Operátor `!` použijte pouze pro třídu nebo rozhraní jako operátor přístupu ke slovníku.</span><span class="sxs-lookup"><span data-stu-id="165a2-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="165a2-137">Třída nebo rozhraní musí mít výchozí vlastnost, která přijímá jeden `String` argument.</span><span class="sxs-lookup"><span data-stu-id="165a2-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="165a2-138">Identifikátor hned za operátorem `!` se bude hodnotou argumentu předanou výchozí vlastnosti jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="165a2-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="165a2-139">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="165a2-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="165a2-140">Tři výstupní řádky `MsgBox` všechny zobrazují `32856`hodnoty.</span><span class="sxs-lookup"><span data-stu-id="165a2-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="165a2-141">První řádek používá tradiční přístup k vlastnosti `index`, druhá využívá fakt, že `index` je výchozí vlastnost `hasDefault`třídy a třetí používá slovník přístup ke třídě.</span><span class="sxs-lookup"><span data-stu-id="165a2-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="165a2-142">Všimněte si, že druhý operand operátoru `!` musí být platný identifikátor Visual Basic, který není uzavřen do dvojitých uvozovek (`" "`).</span><span class="sxs-lookup"><span data-stu-id="165a2-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="165a2-143">Jinými slovy, nelze použít řetězcový literál nebo řetězcovou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="165a2-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="165a2-144">Následující změna na poslední řádek `MsgBox` volání vygeneruje chybu, protože `"X"` je uzavřený řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="165a2-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="165a2-145">Odkazy na výchozí kolekce musí být explicitní.</span><span class="sxs-lookup"><span data-stu-id="165a2-145">References to default collections must be explicit.</span></span> <span data-ttu-id="165a2-146">Konkrétně nelze použít operátor `!` pro proměnnou s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="165a2-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="165a2-147">`!` znak se používá také jako znak `Single` typu.</span><span class="sxs-lookup"><span data-stu-id="165a2-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165a2-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="165a2-148">See also</span></span>

- [<span data-ttu-id="165a2-149">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="165a2-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="165a2-150">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="165a2-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
