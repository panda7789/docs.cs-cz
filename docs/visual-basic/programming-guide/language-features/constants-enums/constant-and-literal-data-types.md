---
title: Datové typy konstanty a literálu
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: b94259326b42104db05d9fc5bb09f686075d0759
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414528"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="73f3f-102">Datové typy konstanty a literálu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73f3f-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="73f3f-103">Literál je hodnota, která je vyjádřena jako samotná, nikoli jako hodnota proměnné nebo výsledek výrazu, například číslo 3 nebo řetězec "Hello".</span><span class="sxs-lookup"><span data-stu-id="73f3f-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="73f3f-104">Konstanta je smysluplný název, který přebírá místo literálu a uchovává stejnou hodnotu v celém programu, na rozdíl od proměnné, jejíž hodnota se může změnit.</span><span class="sxs-lookup"><span data-stu-id="73f3f-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="73f3f-105">Pokud je [možnost odvoditelné](../../../language-reference/statements/option-infer-statement.md) `Off` a [Option Strict](../../../language-reference/statements/option-strict-statement.md) `On` , je nutné explicitně deklarovat všechny konstanty s datovým typem.</span><span class="sxs-lookup"><span data-stu-id="73f3f-105">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="73f3f-106">V následujícím příkladu je datový typ `MyByte` explicitně deklarován jako datový typ `Byte` :</span><span class="sxs-lookup"><span data-stu-id="73f3f-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="73f3f-107">Když `Option Infer` je `On` nebo `Option Strict` `Off` , můžete deklarovat konstantu bez zadání datového typu s `As` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="73f3f-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="73f3f-108">Kompilátor určuje typ konstanty z typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="73f3f-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="73f3f-109">Číselný celočíselný literál je ve výchozím nastavení převeden na `Integer` datový typ.</span><span class="sxs-lookup"><span data-stu-id="73f3f-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="73f3f-110">Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double` a klíčová slova `True` a `False` určují `Boolean` konstantu.</span><span class="sxs-lookup"><span data-stu-id="73f3f-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="73f3f-111">Literály a převod typu</span><span class="sxs-lookup"><span data-stu-id="73f3f-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="73f3f-112">V některých případech můžete chtít vynutit literál na určitý datový typ; například při přiřazování zvláště velké celočíselné literálové hodnoty proměnné typu `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="73f3f-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="73f3f-113">Následující příklad vytvoří chybu:</span><span class="sxs-lookup"><span data-stu-id="73f3f-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="73f3f-114">Chyba je výsledkem reprezentace literálu.</span><span class="sxs-lookup"><span data-stu-id="73f3f-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="73f3f-115">`Decimal`Datový typ může obsahovat hodnotu, která je větší, ale literál je implicitně reprezentován jako `Long` , což nemůže.</span><span class="sxs-lookup"><span data-stu-id="73f3f-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="73f3f-116">Literál můžete převést na konkrétní datový typ dvěma způsoby: připojením znaku typu k tomuto typu nebo jeho umístěním do ohraničujících znaků.</span><span class="sxs-lookup"><span data-stu-id="73f3f-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="73f3f-117">Znak typu nebo ohraničující znaky musí bezprostředně předcházet nebo následovat po literálu, bez mezer nebo znaků jakéhokoliv druhu.</span><span class="sxs-lookup"><span data-stu-id="73f3f-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="73f3f-118">Chcete-li provést předchozí příklad práce, můžete `D` k literálu připojit znak typu, což způsobí, že bude reprezentován jako `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="73f3f-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="73f3f-119">Následující příklad ukazuje správné použití znaků typu a ohraničující znaky:</span><span class="sxs-lookup"><span data-stu-id="73f3f-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="73f3f-120">V následující tabulce jsou uvedeny ohraničující znaky a znaky, které jsou k dispozici v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73f3f-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="73f3f-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="73f3f-121">Data type</span></span>|<span data-ttu-id="73f3f-122">Ohraničující znak</span><span class="sxs-lookup"><span data-stu-id="73f3f-122">Enclosing character</span></span>|<span data-ttu-id="73f3f-123">Znak připojeného typu</span><span class="sxs-lookup"><span data-stu-id="73f3f-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="73f3f-124">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-124">(none)</span></span>|<span data-ttu-id="73f3f-125">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="73f3f-126">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-126">(none)</span></span>|<span data-ttu-id="73f3f-127">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="73f3f-128">"</span><span class="sxs-lookup"><span data-stu-id="73f3f-128">"</span></span>|<span data-ttu-id="73f3f-129">C</span><span class="sxs-lookup"><span data-stu-id="73f3f-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="73f3f-130">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="73f3f-131">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-131">(none)</span></span>|<span data-ttu-id="73f3f-132">D nebo @</span><span class="sxs-lookup"><span data-stu-id="73f3f-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="73f3f-133">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-133">(none)</span></span>|<span data-ttu-id="73f3f-134">R nebo #</span><span class="sxs-lookup"><span data-stu-id="73f3f-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="73f3f-135">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-135">(none)</span></span>|<span data-ttu-id="73f3f-136">I nebo%</span><span class="sxs-lookup"><span data-stu-id="73f3f-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="73f3f-137">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-137">(none)</span></span>|<span data-ttu-id="73f3f-138">L nebo &</span><span class="sxs-lookup"><span data-stu-id="73f3f-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="73f3f-139">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-139">(none)</span></span>|<span data-ttu-id="73f3f-140">S</span><span class="sxs-lookup"><span data-stu-id="73f3f-140">S</span></span>|  
|`Single`|<span data-ttu-id="73f3f-141">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-141">(none)</span></span>|<span data-ttu-id="73f3f-142">F nebo!</span><span class="sxs-lookup"><span data-stu-id="73f3f-142">F or !</span></span>|  
|`String`|<span data-ttu-id="73f3f-143">"</span><span class="sxs-lookup"><span data-stu-id="73f3f-143">"</span></span>|<span data-ttu-id="73f3f-144">(žádná)</span><span class="sxs-lookup"><span data-stu-id="73f3f-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73f3f-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="73f3f-145">See also</span></span>

- [<span data-ttu-id="73f3f-146">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="73f3f-146">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="73f3f-147">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="73f3f-147">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="73f3f-148">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="73f3f-148">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="73f3f-149">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="73f3f-149">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="73f3f-150">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="73f3f-150">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="73f3f-151">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="73f3f-151">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="73f3f-152">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="73f3f-152">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="73f3f-153">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="73f3f-153">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="73f3f-154">Datové typy</span><span class="sxs-lookup"><span data-stu-id="73f3f-154">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="73f3f-155">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="73f3f-155">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
