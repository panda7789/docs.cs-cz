---
title: Priorita operátorů v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: a87407fe863569ff961f4a2dc320e73719ed4d9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601759"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="e903e-102">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e903e-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="e903e-103">Pokud dojde k několika operací ve výrazu, každá část je vyhodnocen a vyřešené v předurčeném pořadí volá *priorita operátorů*.</span><span class="sxs-lookup"><span data-stu-id="e903e-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="e903e-104">Priorita pravidla</span><span class="sxs-lookup"><span data-stu-id="e903e-104">Precedence Rules</span></span>  
 <span data-ttu-id="e903e-105">Výrazy obsahovat operátory z více než jednu kategorii, jsou vyhodnocovány podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="e903e-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="e903e-106">Zřetězení a aritmetické operátory mají pořadí podle priority je popsáno v následující části, a všechny mají vyšší prioritu než relační, logické a bitové operátory.</span><span class="sxs-lookup"><span data-stu-id="e903e-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="e903e-107">Všechny operátory porovnání mají stejnou prioritu a všechny mají vyšší prioritu než logické a bitové operátory, ale nižší prioritu než operátory aritmetické operace a zřetězení.</span><span class="sxs-lookup"><span data-stu-id="e903e-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="e903e-108">Logické a bitové operátory mají pořadí podle priority je popsáno v následující části, a všechny mají nižší prioritu než aritmetické, zřetězení a operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="e903e-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="e903e-109">Operátorů shodné priority jsou vyhodnoceny zleva doprava v pořadí, v jakém jsou uvedeny ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="e903e-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="e903e-110">Pořadí priority</span><span class="sxs-lookup"><span data-stu-id="e903e-110">Precedence Order</span></span>  
 <span data-ttu-id="e903e-111">Operátory jsou vyhodnocovány v následujícím pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="e903e-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="e903e-112">Await – operátor</span><span class="sxs-lookup"><span data-stu-id="e903e-112">Await Operator</span></span>  
 <span data-ttu-id="e903e-113">operátor await</span><span class="sxs-lookup"><span data-stu-id="e903e-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="e903e-114">Aritmetické operátory a operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="e903e-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="e903e-115">Umocnění (`^`)</span><span class="sxs-lookup"><span data-stu-id="e903e-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="e903e-116">Unární identity a negace (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="e903e-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="e903e-117">Násobení a dělení s pohyblivou čárkou (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="e903e-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="e903e-118">Dělení celého čísla (`\`)</span><span class="sxs-lookup"><span data-stu-id="e903e-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="e903e-119">Aritmetické numerického zbytku (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="e903e-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="e903e-120">Sčítání a odčítání (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="e903e-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="e903e-121">Zřetězení řetězců (`&`)</span><span class="sxs-lookup"><span data-stu-id="e903e-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="e903e-122">Aritmetický bitový posun (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="e903e-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="e903e-123">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="e903e-123">Comparison Operators</span></span>  
 <span data-ttu-id="e903e-124">Všechny operátory porovnání (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)</span><span class="sxs-lookup"><span data-stu-id="e903e-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="e903e-125">Logické a bitové operátory</span><span class="sxs-lookup"><span data-stu-id="e903e-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="e903e-126">Negace (`Not`)</span><span class="sxs-lookup"><span data-stu-id="e903e-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="e903e-127">Spojení (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="e903e-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="e903e-128">Inkluzivní disjunkce (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="e903e-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="e903e-129">Exkluzivní disjunkce (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="e903e-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="e903e-130">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e903e-130">Comments</span></span>  
 <span data-ttu-id="e903e-131">`=` Operátor je pouze rovnosti relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e903e-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="e903e-132">Operátoru pro zřetězení řetězců (`&`) není aritmetickém operátoru, ale v prioritu seskupen s aritmetické operátory.</span><span class="sxs-lookup"><span data-stu-id="e903e-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="e903e-133">`Is` a `IsNot` operátory jsou operátory porovnání odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="e903e-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="e903e-134">Neporovnávejte hodnoty dvou objektů přihlášením ke jenom k určení, zda dva objektových proměnných odkazují na stejnou instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="e903e-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="e903e-135">Asociativita</span><span class="sxs-lookup"><span data-stu-id="e903e-135">Associativity</span></span>  
 <span data-ttu-id="e903e-136">Když pohromadě operátory stejnou prioritu ve výrazu, například úlohy násobení a dělení, kompilátor vyhodnocuje každou operaci jako nalezne zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="e903e-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="e903e-137">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e903e-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="e903e-138">První výraz je vyhodnocen jako dělení 96 / 8 (což vede k 12) a potom dělení 12 / 4, což vede k tři.</span><span class="sxs-lookup"><span data-stu-id="e903e-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="e903e-139">Protože kompilátor vyhodnocuje operace pro `n1` zleva doprava, hodnocení je stejný při tomto pořadí explicitně označena pro `n2`.</span><span class="sxs-lookup"><span data-stu-id="e903e-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="e903e-140">Obě `n1` a `n2` mají tři příčiny.</span><span class="sxs-lookup"><span data-stu-id="e903e-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="e903e-141">Naopak `n3` má výsledek 48, protože závorky vynutí vyhodnocení 8 kompilátor / 4 první.</span><span class="sxs-lookup"><span data-stu-id="e903e-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="e903e-142">Kvůli tomuto chování se označují jako operátory *asociativní zleva* v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e903e-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="e903e-143">Přepsání Priorita a asociativita</span><span class="sxs-lookup"><span data-stu-id="e903e-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="e903e-144">Můžete použít závorky k vynucení některé části výrazu, který se má vyhodnotit před ostatními.</span><span class="sxs-lookup"><span data-stu-id="e903e-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="e903e-145">To můžete přepsat v pořadí podle priority a levém asociativity.</span><span class="sxs-lookup"><span data-stu-id="e903e-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="e903e-146">Visual Basic vždy provádí operace, které jsou uzavřeny v závorkách před uživateli mimo.</span><span class="sxs-lookup"><span data-stu-id="e903e-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="e903e-147">Ale v závorkách udržuje běžné přednost a asociativita operátorů, pokud nechcete použít závorky v závorkách.</span><span class="sxs-lookup"><span data-stu-id="e903e-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="e903e-148">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e903e-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e903e-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e903e-149">See also</span></span>
- [<span data-ttu-id="e903e-150">= – operátor</span><span class="sxs-lookup"><span data-stu-id="e903e-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="e903e-151">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="e903e-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="e903e-152">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="e903e-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="e903e-153">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="e903e-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="e903e-154">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="e903e-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="e903e-155">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="e903e-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="e903e-156">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="e903e-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e903e-157">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e903e-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
