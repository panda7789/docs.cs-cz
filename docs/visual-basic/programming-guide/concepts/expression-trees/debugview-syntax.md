---
title: Syntaxe nástroje DebugView vlastností (Visual Basic)
description: Popisuje zvláštní syntaxi vlastností nástroje DebugView k vytvoření řetězcové vyjádření stromů výrazů
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ae2c75607f7b9cdc40fc5c163ce533f0472ab454
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689537"
---
# <a name="debugview-syntax"></a><span data-ttu-id="36536-103">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36536-103">`DebugView` syntax</span></span>

<span data-ttu-id="36536-104">`DebugView` (K dispozici pouze při ladění) obsahuje řetězec vykreslování stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="36536-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="36536-105">Většina syntaxe je celkem jasné, abyste pochopili; zvláštní případy jsou popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="36536-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="36536-106">Každý příklad následuje obsahující blok komentáře `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="36536-106">Each example is followed by a comment block containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="36536-107">Výraz ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="36536-107">ParameterExpression</span></span>

<span data-ttu-id="36536-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="36536-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="36536-109">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="36536-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="36536-110">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="36536-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="36536-111">ConstantExpressions</span></span>

<span data-ttu-id="36536-112">Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="36536-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="36536-113">Pro některé číselné typy se přidá přípona k hodnotě:</span><span class="sxs-lookup"><span data-stu-id="36536-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="36536-114">Type</span><span class="sxs-lookup"><span data-stu-id="36536-114">Type</span></span> | <span data-ttu-id="36536-115">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="36536-115">Keyword</span></span> | <span data-ttu-id="36536-116">Přípona</span><span class="sxs-lookup"><span data-stu-id="36536-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="36536-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="36536-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="36536-118">U</span><span class="sxs-lookup"><span data-stu-id="36536-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="36536-119">Long</span><span class="sxs-lookup"><span data-stu-id="36536-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="36536-120">L</span><span class="sxs-lookup"><span data-stu-id="36536-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="36536-121">ULong</span><span class="sxs-lookup"><span data-stu-id="36536-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="36536-122">UL</span><span class="sxs-lookup"><span data-stu-id="36536-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="36536-123">Double</span><span class="sxs-lookup"><span data-stu-id="36536-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="36536-124">D</span><span class="sxs-lookup"><span data-stu-id="36536-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="36536-125">Jeden</span><span class="sxs-lookup"><span data-stu-id="36536-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="36536-126">F</span><span class="sxs-lookup"><span data-stu-id="36536-126">F</span></span> |
| <xref:System.Decimal> | [<span data-ttu-id="36536-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="36536-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="36536-128">M</span><span class="sxs-lookup"><span data-stu-id="36536-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="36536-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="36536-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="36536-130">BlockExpression</span></span>

<span data-ttu-id="36536-131">Pokud typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objektu se liší od typu posledního výrazu v bloku, zobrazí se typ v lomených závorkách (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="36536-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="36536-132">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="36536-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="36536-133">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="36536-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="36536-134">LambdaExpression</span></span>

<span data-ttu-id="36536-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="36536-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="36536-136">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="36536-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="36536-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="36536-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="36536-138">LabelExpression</span></span>

<span data-ttu-id="36536-139">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="36536-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="36536-140">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="36536-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="36536-141">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="36536-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="36536-142">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="36536-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="36536-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="36536-144">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="36536-144">Checked Operators</span></span>

<span data-ttu-id="36536-145">Checked operátory jsou zobrazovány `#` symbol před operátor.</span><span class="sxs-lookup"><span data-stu-id="36536-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="36536-146">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="36536-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="36536-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="36536-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
