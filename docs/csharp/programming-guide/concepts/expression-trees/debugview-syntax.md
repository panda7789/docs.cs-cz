---
title: Syntaxe používaná vlastností DebugView (C#)
description: Popisuje speciální syntaxi použitou vlastností DebugView k vytvoření řetězcové reprezentace stromů výrazů.
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "67661719"
---
# <a name="debugview-syntax"></a><span data-ttu-id="f7dc2-103">`DebugView`Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7dc2-103">`DebugView` syntax</span></span>

<span data-ttu-id="f7dc2-104">Vlastnost `DebugView` (k dispozici pouze při ladění) poskytuje vykreslování řetězce stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="f7dc2-105">Většina syntaxe je poměrně jednoduché pochopit; zvláštní případy jsou popsány v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="f7dc2-106">Za každým příkladem následuje blokový komentář `DebugView`obsahující .</span><span class="sxs-lookup"><span data-stu-id="f7dc2-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="f7dc2-107">Parameterexpression</span><span class="sxs-lookup"><span data-stu-id="f7dc2-107">ParameterExpression</span></span>

<span data-ttu-id="f7dc2-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>názvy proměnných jsou `$` zobrazeny se symbolem na začátku.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="f7dc2-109">Pokud parametr nemá název, je mu přiřazen automaticky generovaný `$var1` `$var2`název, například nebo .</span><span class="sxs-lookup"><span data-stu-id="f7dc2-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="f7dc2-110">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="f7dc2-111">Constantexpression</span><span class="sxs-lookup"><span data-stu-id="f7dc2-111">ConstantExpression</span></span>

<span data-ttu-id="f7dc2-112">Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které představují celé hodnoty, řetězce a `null`, je zobrazena hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="f7dc2-113">Pro číselné typy, které mají standardní přípony jako literály jazyka C#, je přípona přidána k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="f7dc2-114">V následující tabulce jsou uvedeny přípony přidružené k různým číselným typům.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="f7dc2-115">Typ</span><span class="sxs-lookup"><span data-stu-id="f7dc2-115">Type</span></span> | <span data-ttu-id="f7dc2-116">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="f7dc2-116">Keyword</span></span> | <span data-ttu-id="f7dc2-117">Přípona</span><span class="sxs-lookup"><span data-stu-id="f7dc2-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-118">uint</span><span class="sxs-lookup"><span data-stu-id="f7dc2-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="f7dc2-119">U</span><span class="sxs-lookup"><span data-stu-id="f7dc2-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-120">long</span><span class="sxs-lookup"><span data-stu-id="f7dc2-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="f7dc2-121">L</span><span class="sxs-lookup"><span data-stu-id="f7dc2-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-122">ulong</span><span class="sxs-lookup"><span data-stu-id="f7dc2-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="f7dc2-123">UL</span><span class="sxs-lookup"><span data-stu-id="f7dc2-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-124">double</span><span class="sxs-lookup"><span data-stu-id="f7dc2-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="f7dc2-125">D</span><span class="sxs-lookup"><span data-stu-id="f7dc2-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-126">float</span><span class="sxs-lookup"><span data-stu-id="f7dc2-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="f7dc2-127">F</span><span class="sxs-lookup"><span data-stu-id="f7dc2-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="f7dc2-128">decimal</span><span class="sxs-lookup"><span data-stu-id="f7dc2-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="f7dc2-129">M</span><span class="sxs-lookup"><span data-stu-id="f7dc2-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="f7dc2-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-130">Examples</span></span>

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="f7dc2-131">Blockexpression</span><span class="sxs-lookup"><span data-stu-id="f7dc2-131">BlockExpression</span></span>

<span data-ttu-id="f7dc2-132">Pokud se typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objektu liší od typu posledního výrazu v bloku, zobrazí se`<` `>`text v rámci úhlových závorek ( a ).</span><span class="sxs-lookup"><span data-stu-id="f7dc2-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="f7dc2-133">V opačném případě <xref:System.Linq.Expressions.BlockExpression> se nezobrazí typ objektu.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="f7dc2-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-134">Examples</span></span>

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="f7dc2-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="f7dc2-135">LambdaExpression</span></span>

<span data-ttu-id="f7dc2-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>objekty jsou zobrazeny společně s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="f7dc2-137">Pokud výraz lambda nemá název, je mu přiřazen automaticky generovaný název, například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="f7dc2-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a><span data-ttu-id="f7dc2-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="f7dc2-139">LabelExpression</span></span>

<span data-ttu-id="f7dc2-140">Pokud zadáte výchozí hodnotu <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> objektu, tato hodnota <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> se zobrazí před objektem.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="f7dc2-141">Token `.Label` označuje začátek popisku.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="f7dc2-142">Token `.LabelTarget` označuje cíl cíle, na který chcete přejít.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="f7dc2-143">Pokud popisek nemá název, je mu přiřazen automaticky generovaný název, například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="f7dc2-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a><span data-ttu-id="f7dc2-145">Kontrolované operátory</span><span class="sxs-lookup"><span data-stu-id="f7dc2-145">Checked Operators</span></span>

<span data-ttu-id="f7dc2-146">Kontrolované operátory jsou zobrazeny se symbolem `#` před operátorem.</span><span class="sxs-lookup"><span data-stu-id="f7dc2-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="f7dc2-147">Například operátor checked sčítání se `#+`zobrazí jako .</span><span class="sxs-lookup"><span data-stu-id="f7dc2-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="f7dc2-148">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7dc2-148">Examples</span></span>

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
