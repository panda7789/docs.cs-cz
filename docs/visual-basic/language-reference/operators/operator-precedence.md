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
ms.openlocfilehash: df40aced45442c9c7895c8d10ece64b21e292508
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659927"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="3d54a-102">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d54a-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="3d54a-103">Když ve výrazu dojde k několika operacím, každá část je vyhodnocena a vyřešena v předem určeném pořadí s názvem *Priorita operátora*.</span><span class="sxs-lookup"><span data-stu-id="3d54a-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="3d54a-104">Pravidla priorit</span><span class="sxs-lookup"><span data-stu-id="3d54a-104">Precedence Rules</span></span>
 <span data-ttu-id="3d54a-105">Když výrazy obsahují operátory z více než jedné kategorie, vyhodnotí se podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="3d54a-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="3d54a-106">Operátory aritmetické a zřetězení mají pořadí priority popsané v následující části a všechny mají větší prioritu než porovnání, logické a bitové operátory.</span><span class="sxs-lookup"><span data-stu-id="3d54a-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="3d54a-107">Všechny operátory porovnání mají stejnou přednost a všechny mají větší prioritu než logické a bitové operátory, ale nižší prioritu než operátory aritmetické a zřetězení.</span><span class="sxs-lookup"><span data-stu-id="3d54a-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="3d54a-108">Logické a bitové operátory mají pořadí priority popsané v následující části a všechny mají nižší prioritu než aritmetické operátory, zřetězení a porovnání.</span><span class="sxs-lookup"><span data-stu-id="3d54a-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="3d54a-109">Operátory s stejnou prioritou jsou vyhodnocovány zleva doprava v pořadí, ve kterém jsou uvedeny ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d54a-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="3d54a-110">Pořadí priority</span><span class="sxs-lookup"><span data-stu-id="3d54a-110">Precedence Order</span></span>
 <span data-ttu-id="3d54a-111">Operátory jsou vyhodnocovány v následujícím pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="3d54a-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="3d54a-112">Await – operátor</span><span class="sxs-lookup"><span data-stu-id="3d54a-112">Await Operator</span></span>
 <span data-ttu-id="3d54a-113">Await</span><span class="sxs-lookup"><span data-stu-id="3d54a-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="3d54a-114">Operátory aritmetického operátoru and zřetězení</span><span class="sxs-lookup"><span data-stu-id="3d54a-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="3d54a-115">Umocnění`^`()</span><span class="sxs-lookup"><span data-stu-id="3d54a-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="3d54a-116">Unární identita a negace (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="3d54a-117">Násobení a dělení plovoucí desetinné čárky`*`( `/`,)</span><span class="sxs-lookup"><span data-stu-id="3d54a-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="3d54a-118">Celočíselné dělení`\`()</span><span class="sxs-lookup"><span data-stu-id="3d54a-118">Integer division (`\`)</span></span>

 <span data-ttu-id="3d54a-119">Modulární aritmetická`Mod`operace ()</span><span class="sxs-lookup"><span data-stu-id="3d54a-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="3d54a-120">Sčítání a odčítání (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="3d54a-121">Zřetězení řetězců (`&`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="3d54a-122">Aritmetický přenosový`<<`posun `>>`(,)</span><span class="sxs-lookup"><span data-stu-id="3d54a-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="3d54a-123">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="3d54a-123">Comparison Operators</span></span>
 <span data-ttu-id="3d54a-124">Všechny operátory porovnání (`=`, `<>`, `<` `<=`,, `>`, ,,`Is`,, .`TypeOf`.. `IsNot` `>=` `Like` `Is`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="3d54a-125">Logické a bitové operátory</span><span class="sxs-lookup"><span data-stu-id="3d54a-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="3d54a-126">Negace (`Not`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-126">Negation (`Not`)</span></span>

 <span data-ttu-id="3d54a-127">Spojení (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="3d54a-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="3d54a-128">Celková odvýšení`Or`( `OrElse`,)</span><span class="sxs-lookup"><span data-stu-id="3d54a-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="3d54a-129">Exkluzivní disjunkení`Xor`()</span><span class="sxs-lookup"><span data-stu-id="3d54a-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="3d54a-130">Komentáře</span><span class="sxs-lookup"><span data-stu-id="3d54a-130">Comments</span></span>
 <span data-ttu-id="3d54a-131">`=` Operátor je pouze operátor porovnání rovnosti, nikoli operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3d54a-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="3d54a-132">Operátor zřetězení řetězce (`&`) není aritmetickým operátorem, ale v prioritě je seskupen s aritmetickými operátory.</span><span class="sxs-lookup"><span data-stu-id="3d54a-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="3d54a-133">Operátory `Is` a`IsNot` jsou operátory porovnání odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="3d54a-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="3d54a-134">Nerovnávají hodnoty dvou objektů; kontrolují pouze k určení, zda dvě proměnné objektu odkazují na stejnou instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="3d54a-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="3d54a-135">Asociativita</span><span class="sxs-lookup"><span data-stu-id="3d54a-135">Associativity</span></span>
 <span data-ttu-id="3d54a-136">Pokud se operátory stejné priority zobrazí společně ve výrazu, například násobení a dělení, kompilátor vyhodnotí každou operaci jako v případě, že ji narazí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="3d54a-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="3d54a-137">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3d54a-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="3d54a-138">První výraz vyhodnotí divizi 96/8 (což má za následek 12) a potom rozdělením 12/4, které má za následek tři.</span><span class="sxs-lookup"><span data-stu-id="3d54a-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="3d54a-139">Vzhledem k tomu, že kompilátor vyhodnocuje `n1` operace od zleva doprava, je vyhodnocení stejné, pokud je pořadí explicitně určeno pro. `n2`</span><span class="sxs-lookup"><span data-stu-id="3d54a-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="3d54a-140">`n1` A`n2` mají výsledek tři.</span><span class="sxs-lookup"><span data-stu-id="3d54a-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="3d54a-141">Naproti tomu `n3` má výsledek 48, protože kulaté závorky vynutí, aby kompilátor vyhodnotil 8/4 jako první.</span><span class="sxs-lookup"><span data-stu-id="3d54a-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="3d54a-142">Z důvodu tohoto chování jsou operátory označeny jako *asociativní* v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3d54a-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="3d54a-143">Přepsání priority a asociativita</span><span class="sxs-lookup"><span data-stu-id="3d54a-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="3d54a-144">Pomocí závorek můžete vynutit, aby některé části výrazu byly vyhodnoceny před jinými.</span><span class="sxs-lookup"><span data-stu-id="3d54a-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="3d54a-145">To může přepsat pořadí priorit i levou asociativita.</span><span class="sxs-lookup"><span data-stu-id="3d54a-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="3d54a-146">Visual Basic vždy provádí operace, které jsou uzavřeny v závorkách před těmito objekty mimo.</span><span class="sxs-lookup"><span data-stu-id="3d54a-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="3d54a-147">V závorkách však udržuje běžnou prioritu a asociativita, pokud v závorkách nepoužíváte závorky.</span><span class="sxs-lookup"><span data-stu-id="3d54a-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="3d54a-148">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3d54a-148">The following example illustrates this.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="3d54a-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d54a-149">See also</span></span>

- [<span data-ttu-id="3d54a-150">= – operátor</span><span class="sxs-lookup"><span data-stu-id="3d54a-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="3d54a-151">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="3d54a-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="3d54a-152">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="3d54a-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="3d54a-153">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="3d54a-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="3d54a-154">Operátor Typeof</span><span class="sxs-lookup"><span data-stu-id="3d54a-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="3d54a-155">Operátor Await</span><span class="sxs-lookup"><span data-stu-id="3d54a-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="3d54a-156">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="3d54a-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3d54a-157">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="3d54a-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
