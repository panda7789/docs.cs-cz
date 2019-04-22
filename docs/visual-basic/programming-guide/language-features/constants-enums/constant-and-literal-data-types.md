---
title: Datové typy konstanty a literálu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 50e36aa13439bafcca27a7153a8c5d6043f03975
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833500"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="69a23-102">Datové typy konstanty a literálu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69a23-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="69a23-103">Literál je hodnota, která je vyjádřena jako samotný, nikoli jako hodnota proměnné nebo výsledku výrazu, například číslo 3 nebo řetězec "Hello".</span><span class="sxs-lookup"><span data-stu-id="69a23-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="69a23-104">Konstanta je smysluplný název, který probíhá literály a ponechá tato stejná hodnota v celém programu, na rozdíl od proměnné, jejíž hodnota se může změnit.</span><span class="sxs-lookup"><span data-stu-id="69a23-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="69a23-105">Když [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, je třeba deklarovat všechny konstanty explicitně s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="69a23-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="69a23-106">V následujícím příkladu, datový typ `MyByte` je explicitně deklarována jako datový typ `Byte`:</span><span class="sxs-lookup"><span data-stu-id="69a23-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="69a23-107">Když `Option Infer` je `On` nebo `Option Strict` je `Off`, je možné deklarovat konstanty bez zadání datový typ s `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="69a23-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="69a23-108">Kompilátor Určuje typ konstanty z typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="69a23-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="69a23-109">Ve výchozím nastavení je přetypování číselné celočíselný literál `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="69a23-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="69a23-110">Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double`a klíčová slova `True` a `False` zadat `Boolean` konstantní.</span><span class="sxs-lookup"><span data-stu-id="69a23-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="69a23-111">Literály a převod typu</span><span class="sxs-lookup"><span data-stu-id="69a23-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="69a23-112">V některých případech můžete chtít vynutit literál na konkrétní datový typ; například při přiřazování k proměnné typu zejména velkou celočíselnou hodnotu literálu `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="69a23-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="69a23-113">Následující příklad generuje chybu:</span><span class="sxs-lookup"><span data-stu-id="69a23-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="69a23-114">Chyba výsledků z reprezentace literál.</span><span class="sxs-lookup"><span data-stu-id="69a23-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="69a23-115">`Decimal` Datový typ může obsahovat hodnotu velké, ale literálu je implicitně reprezentována jako `Long`, které nemohou.</span><span class="sxs-lookup"><span data-stu-id="69a23-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="69a23-116">Můžete vynucení literál na konkrétní datový typ dvěma způsoby: přidáním znaku typu nebo tak, že v rámci nadřazené znaků.</span><span class="sxs-lookup"><span data-stu-id="69a23-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="69a23-117">Znak typu nebo orámování znaků musí bezprostředně předcházet nebo postupujte podle literál bez použité místo nebo znaky jakéhokoli druhu.</span><span class="sxs-lookup"><span data-stu-id="69a23-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="69a23-118">Aby předchozí příklad pracovat, můžete připojit `D` zadejte znak pro literál, který způsobí, že aby se dala vyjádřit jako `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="69a23-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="69a23-119">Následující příklad ukazuje správné použití typu a nadřazeného znaků:</span><span class="sxs-lookup"><span data-stu-id="69a23-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="69a23-120">Následující tabulka uvádí nadřazeného znaky a znaky typu, které jsou k dispozici v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="69a23-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="69a23-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="69a23-121">Data type</span></span>|<span data-ttu-id="69a23-122">Vnější znak</span><span class="sxs-lookup"><span data-stu-id="69a23-122">Enclosing character</span></span>|<span data-ttu-id="69a23-123">Znak typu připojený</span><span class="sxs-lookup"><span data-stu-id="69a23-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="69a23-124">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-124">(none)</span></span>|<span data-ttu-id="69a23-125">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="69a23-126">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-126">(none)</span></span>|<span data-ttu-id="69a23-127">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="69a23-128">"</span><span class="sxs-lookup"><span data-stu-id="69a23-128">"</span></span>|<span data-ttu-id="69a23-129">C</span><span class="sxs-lookup"><span data-stu-id="69a23-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="69a23-130">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="69a23-131">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-131">(none)</span></span>|<span data-ttu-id="69a23-132">D nebo @</span><span class="sxs-lookup"><span data-stu-id="69a23-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="69a23-133">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-133">(none)</span></span>|<span data-ttu-id="69a23-134">R nebo #</span><span class="sxs-lookup"><span data-stu-id="69a23-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="69a23-135">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-135">(none)</span></span>|<span data-ttu-id="69a23-136">Nebo %</span><span class="sxs-lookup"><span data-stu-id="69a23-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="69a23-137">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-137">(none)</span></span>|<span data-ttu-id="69a23-138">L nebo &</span><span class="sxs-lookup"><span data-stu-id="69a23-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="69a23-139">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-139">(none)</span></span>|<span data-ttu-id="69a23-140">S</span><span class="sxs-lookup"><span data-stu-id="69a23-140">S</span></span>|  
|`Single`|<span data-ttu-id="69a23-141">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-141">(none)</span></span>|<span data-ttu-id="69a23-142">F nebo!</span><span class="sxs-lookup"><span data-stu-id="69a23-142">F or !</span></span>|  
|`String`|<span data-ttu-id="69a23-143">"</span><span class="sxs-lookup"><span data-stu-id="69a23-143">"</span></span>|<span data-ttu-id="69a23-144">(žádné)</span><span class="sxs-lookup"><span data-stu-id="69a23-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69a23-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69a23-145">See also</span></span>

- [<span data-ttu-id="69a23-146">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="69a23-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [<span data-ttu-id="69a23-147">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="69a23-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [<span data-ttu-id="69a23-148">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="69a23-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="69a23-149">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="69a23-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="69a23-150">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="69a23-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="69a23-151">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="69a23-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="69a23-152">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="69a23-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="69a23-153">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="69a23-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="69a23-154">Datové typy</span><span class="sxs-lookup"><span data-stu-id="69a23-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="69a23-155">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="69a23-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
