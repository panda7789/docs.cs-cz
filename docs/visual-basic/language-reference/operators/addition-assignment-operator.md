---
title: += – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372204"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="cf3ef-102">+= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf3ef-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="cf3ef-103">Přidá hodnotu číselného výrazu do hodnoty číselné proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="cf3ef-104">Lze také použít ke zřetězení `String` výrazu s `String` proměnnou nebo vlastností a přiřazení výsledku k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf3ef-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cf3ef-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="cf3ef-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="cf3ef-107">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-107">Required.</span></span> <span data-ttu-id="cf3ef-108">Jakákoli číselná nebo `String` proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="cf3ef-109">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-109">Required.</span></span> <span data-ttu-id="cf3ef-110">Libovolný číselný `String` výraz or.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf3ef-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf3ef-111">Remarks</span></span>  
 <span data-ttu-id="cf3ef-112">Element na levé straně `+=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="cf3ef-113">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ef-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="cf3ef-114">`+=`Operátor přidá hodnotu na pravé straně k proměnné nebo vlastnosti vlevo a výsledek přiřadí proměnné nebo vlastnosti nalevo.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="cf3ef-115">`+=`Operátor lze také použít k zřetězení `String` výrazu na základě jeho práva na `String` proměnnou nebo vlastnost vlevo a přiřazení výsledku k proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf3ef-116">Při použití `+=` operátoru nemusí být možné určit, zda dojde k přidání nebo zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="cf3ef-117">Použijte `&=` operátor pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro samoobslužné dokumenty.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="cf3ef-118">Tento operátor přiřazení implicitně provádí rozšiřující, ale ne zužující převody, pokud prostředí kompilace vynutilo striktní sémantiku.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="cf3ef-119">Další informace o těchto převodech naleznete v tématu [rozšiřující a zúžené převody](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ef-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="cf3ef-120">Další informace o striktní a opravňující sémantikě naleznete v tématu [Option Strict Statement](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ef-120">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="cf3ef-121">Pokud je povolená sémantika povolující, `+=` operátor implicitně provede celou řadu řetězců a číselných převodů, které jsou stejné jako u `+` operátorů.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="cf3ef-122">Podrobnosti o těchto převodech naleznete v tématu [+ Operator](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ef-122">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cf3ef-123">Přetížení</span><span class="sxs-lookup"><span data-stu-id="cf3ef-123">Overloading</span></span>  
 <span data-ttu-id="cf3ef-124">`+`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cf3ef-125">Přetížení `+` operátoru ovlivňuje chování `+=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="cf3ef-126">Pokud váš kód používá `+=` pro třídu nebo strukturu, která je přetížena `+` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cf3ef-127">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ef-127">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf3ef-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf3ef-128">Example</span></span>  
 <span data-ttu-id="cf3ef-129">Následující příklad používá `+=` operátor ke kombinování hodnoty jedné proměnné s jinou.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="cf3ef-130">První část používá `+=` s číselnými proměnnými k přidání jedné hodnoty do druhé.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="cf3ef-131">Druhá část používá `+=` s `String` proměnnými k zřetězení jedné hodnoty s jinou.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="cf3ef-132">V obou případech je výsledek přiřazen první proměnné.</span><span class="sxs-lookup"><span data-stu-id="cf3ef-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="cf3ef-133">Hodnota `num1` je nyní 13 a hodnota `str1` je nyní "103".</span><span class="sxs-lookup"><span data-stu-id="cf3ef-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3ef-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf3ef-134">See also</span></span>

- [<span data-ttu-id="cf3ef-135">+ – Operátor</span><span class="sxs-lookup"><span data-stu-id="cf3ef-135">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="cf3ef-136">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="cf3ef-136">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="cf3ef-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="cf3ef-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="cf3ef-138">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="cf3ef-138">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="cf3ef-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf3ef-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="cf3ef-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="cf3ef-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="cf3ef-141">Příkazy</span><span class="sxs-lookup"><span data-stu-id="cf3ef-141">Statements</span></span>](../../programming-guide/language-features/statements.md)
