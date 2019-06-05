---
title: Syntaxe vlastností nástroje DebugView (C#)
description: Popisuje zvláštní syntaxi vlastností nástroje DebugView k vytvoření řetězcové vyjádření stromů výrazů
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: bc3fc579ed8031d818241f41ac728ef7e5be0b99
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690108"
---
# <a name="debugview-syntax"></a><span data-ttu-id="85a71-103">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85a71-103">`DebugView` syntax</span></span>

<span data-ttu-id="85a71-104">`DebugView` (K dispozici pouze při ladění) obsahuje řetězec vykreslování stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="85a71-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="85a71-105">Většina syntaxe je celkem jasné, abyste pochopili; zvláštní případy jsou popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="85a71-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="85a71-106">Každý příklad následuje blok komentáře, který obsahuje `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="85a71-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="85a71-107">Výraz ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="85a71-107">ParameterExpression</span></span>

<span data-ttu-id="85a71-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> se zobrazují názvy proměnných `$` symbolu na počátku.</span><span class="sxs-lookup"><span data-stu-id="85a71-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="85a71-109">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="85a71-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="85a71-110">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="85a71-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="85a71-111">ConstantExpression</span></span>

<span data-ttu-id="85a71-112">Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="85a71-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="85a71-113">Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="85a71-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="85a71-114">V následující tabulce jsou uvedeny přípony spojené s různé číselné typy.</span><span class="sxs-lookup"><span data-stu-id="85a71-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="85a71-115">Type</span><span class="sxs-lookup"><span data-stu-id="85a71-115">Type</span></span> | <span data-ttu-id="85a71-116">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="85a71-116">Keyword</span></span> | <span data-ttu-id="85a71-117">Přípona</span><span class="sxs-lookup"><span data-stu-id="85a71-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="85a71-118">uint</span><span class="sxs-lookup"><span data-stu-id="85a71-118">uint</span></span>](../../../language-reference/keywords/uint.md) | <span data-ttu-id="85a71-119">U</span><span class="sxs-lookup"><span data-stu-id="85a71-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="85a71-120">long</span><span class="sxs-lookup"><span data-stu-id="85a71-120">long</span></span>](../../../language-reference/keywords/long.md) | <span data-ttu-id="85a71-121">L</span><span class="sxs-lookup"><span data-stu-id="85a71-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="85a71-122">ulong</span><span class="sxs-lookup"><span data-stu-id="85a71-122">ulong</span></span>](../../../language-reference/keywords/ulong.md) | <span data-ttu-id="85a71-123">UL</span><span class="sxs-lookup"><span data-stu-id="85a71-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="85a71-124">double</span><span class="sxs-lookup"><span data-stu-id="85a71-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="85a71-125">D</span><span class="sxs-lookup"><span data-stu-id="85a71-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="85a71-126">float</span><span class="sxs-lookup"><span data-stu-id="85a71-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="85a71-127">F</span><span class="sxs-lookup"><span data-stu-id="85a71-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="85a71-128">decimal</span><span class="sxs-lookup"><span data-stu-id="85a71-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="85a71-129">M</span><span class="sxs-lookup"><span data-stu-id="85a71-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="85a71-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="85a71-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="85a71-131">BlockExpression</span></span>

<span data-ttu-id="85a71-132">Pokud typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objektu se liší od typu posledního výrazu v bloku, zobrazí se typ v lomených závorkách (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="85a71-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="85a71-133">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="85a71-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="85a71-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="85a71-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="85a71-135">LambdaExpression</span></span>

<span data-ttu-id="85a71-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="85a71-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="85a71-137">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="85a71-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="85a71-138">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="85a71-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="85a71-139">LabelExpression</span></span>

<span data-ttu-id="85a71-140">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="85a71-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="85a71-141">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="85a71-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="85a71-142">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="85a71-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="85a71-143">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="85a71-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="85a71-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="85a71-145">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="85a71-145">Checked Operators</span></span>

<span data-ttu-id="85a71-146">Checked operátory jsou zobrazovány `#` symbol před operátor.</span><span class="sxs-lookup"><span data-stu-id="85a71-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="85a71-147">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="85a71-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="85a71-148">Příklady</span><span class="sxs-lookup"><span data-stu-id="85a71-148">Examples</span></span>

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
