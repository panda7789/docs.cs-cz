---
title: Operators – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: fd10999066f599d819ef188e09028c64c6a5e9e6
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65064044"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="5c912-102">Operátory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5c912-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="5c912-103">V jazyce C# *operátor* je prvek programu, který se použije pro jeden nebo několik *operandy* ve výrazu nebo příkazu.</span><span class="sxs-lookup"><span data-stu-id="5c912-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="5c912-104">Operátory, které používají jeden operand, jako je operátor Inkrementace (`++`) nebo `new`, jsou označovány jako *unární* operátory.</span><span class="sxs-lookup"><span data-stu-id="5c912-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="5c912-105">Operátory, které používají dva operandy, jako jsou aritmetické operátory (`+`,`-`,`*`,`/`), jsou označovány jako *binární* operátory.</span><span class="sxs-lookup"><span data-stu-id="5c912-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="5c912-106">Jeden z operátorů, podmiňovací operátor (`?:`), má tři operandy a je jediným ternárním operátorem v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="5c912-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="5c912-107">Následující příkaz jazyka C# obsahuje jeden unární operátor a jeden operand.</span><span class="sxs-lookup"><span data-stu-id="5c912-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="5c912-108">Operátor Inkrementace `++`, upravuje hodnotu operandu `y`.</span><span class="sxs-lookup"><span data-stu-id="5c912-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="5c912-109">Následující příkaz jazyka C# obsahuje dva binární operátory, z nichž každý používá dva operandy.</span><span class="sxs-lookup"><span data-stu-id="5c912-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="5c912-110">Operátor přiřazení `=`, má celočíselné proměnné `y` a výraz `2 + 3` jako operandy.</span><span class="sxs-lookup"><span data-stu-id="5c912-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="5c912-111">Výraz `2 + 3` samotné se skládá z operátoru sčítání a dvou operandů `2` a `3`.</span><span class="sxs-lookup"><span data-stu-id="5c912-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="5c912-112">Operand může být platný výraz, který se skládá z jakékoli délky kódu a který může zahrnovat libovolný počet dílčích výrazů.</span><span class="sxs-lookup"><span data-stu-id="5c912-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="5c912-113">Ve výrazu, který obsahuje více operátorů je pořadí použití operátorů určeno *priorita operátorů*, *asociativita*a závorky.</span><span class="sxs-lookup"><span data-stu-id="5c912-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="5c912-114">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="5c912-114">Operator precedence</span></span>
  
<span data-ttu-id="5c912-115">Jednotlivé operátory mají definovanou prioritu.</span><span class="sxs-lookup"><span data-stu-id="5c912-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="5c912-116">Ve výrazu s větším počtem operátorů, které mají odlišnou prioritu, určuje priorita operátorů pořadí, ve kterém jsou operátory vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="5c912-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="5c912-117">Například následující příkaz přiřadí 3 `n1`:</span><span class="sxs-lookup"><span data-stu-id="5c912-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="5c912-118">Nejdříve je provedeno násobení, protože násobení má přednost před odčítáním.</span><span class="sxs-lookup"><span data-stu-id="5c912-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="5c912-119">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c912-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="5c912-120">Asociativita</span><span class="sxs-lookup"><span data-stu-id="5c912-120">Associativity</span></span>

 <span data-ttu-id="5c912-121">Pokud výraz obsahuje dva nebo více operátorů se stejnou prioritou, jsou vyhodnocovány na základě asociativity.</span><span class="sxs-lookup"><span data-stu-id="5c912-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="5c912-122">Operátory asociativní zleva se vyhodnocují v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="5c912-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="5c912-123">Například `x * y / z` se vyhodnotí jako `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="5c912-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="5c912-124">Operátory asociativní zprava se vyhodnocují v pořadí zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="5c912-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="5c912-125">Například operátor přiřazení je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="5c912-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="5c912-126">Pokud by nebyl, následující kód by způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="5c912-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="5c912-127">Další příklad tříhodnotový operátor ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="5c912-127">As another example the ternary operator ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="5c912-128">Většina binární operátory jsou asociativní zleva.</span><span class="sxs-lookup"><span data-stu-id="5c912-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="5c912-129">Ať už jsou operátory ve výrazu asociativní zleva nebo asociativní zprava, jsou nejdříve vyhodnocovány operandy jednotlivých výrazů, zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="5c912-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="5c912-130">Následující příklady znázorňují pořadí vyhodnocení operátorů a operandů.</span><span class="sxs-lookup"><span data-stu-id="5c912-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="5c912-131">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5c912-131">Statement</span></span>|<span data-ttu-id="5c912-132">Pořadí vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="5c912-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="5c912-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="5c912-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="5c912-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="5c912-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="5c912-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="5c912-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="5c912-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="5c912-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="5c912-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="5c912-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="5c912-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="5c912-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="5c912-139">Přidávání závorek</span><span class="sxs-lookup"><span data-stu-id="5c912-139">Adding parentheses</span></span>

 <span data-ttu-id="5c912-140">Pořadí stanovené na základě priority operátorů a asociativity můžete změnit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="5c912-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="5c912-141">Například `2 + 3 * 2` obvykle vyhodnocen jako 8, protože operátory násobení přednost před operátory sčítání.</span><span class="sxs-lookup"><span data-stu-id="5c912-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="5c912-142">Nicméně pokud napíšete výraz jako `(2 + 3) * 2`, sčítání je vyhodnoceno před násobením a výsledkem je 10.</span><span class="sxs-lookup"><span data-stu-id="5c912-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="5c912-143">Následující příklady znázorňují pořadí vyhodnocení ve výrazech se závorkami.</span><span class="sxs-lookup"><span data-stu-id="5c912-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="5c912-144">Stejně jako v předchozích příkladech se operandy vyhodnocují ještě před použitím operátoru.</span><span class="sxs-lookup"><span data-stu-id="5c912-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="5c912-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="5c912-145">Statement</span></span>|<span data-ttu-id="5c912-146">Pořadí vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="5c912-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="5c912-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="5c912-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="5c912-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="5c912-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="5c912-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="5c912-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="5c912-150">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="5c912-150">Operator overloading</span></span>

<span data-ttu-id="5c912-151">Můžete definovat chování určitých operátorů pro vlastní třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="5c912-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="5c912-152">Tento proces se označuje jako *přetížení operátoru*.</span><span class="sxs-lookup"><span data-stu-id="5c912-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="5c912-153">Další informace najdete v tématu [přetížitelné operátory](overloadable-operators.md) a [operátor](../../language-reference/keywords/operator.md) článku – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5c912-153">For more information, see [Overloadable operators](overloadable-operators.md) and the [operator](../../language-reference/keywords/operator.md) keyword article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5c912-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c912-154">See also</span></span>

- [<span data-ttu-id="5c912-155">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5c912-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5c912-156">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="5c912-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="5c912-157">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5c912-157">C# Operators</span></span>](../../language-reference/operators/index.md)
- [<span data-ttu-id="5c912-158">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="5c912-158">Operator Keywords</span></span>](../../language-reference/keywords/operator-keywords.md)
