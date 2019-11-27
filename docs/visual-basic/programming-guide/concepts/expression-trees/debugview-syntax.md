---
title: Syntaxe používaná vlastností nástroj DebugView
description: Popisuje speciální syntaxi používanou vlastností nástroj DebugView k vytvoření řetězcové reprezentace stromů výrazů.
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 98ceba37aa226fab68ae1c1028e2a1139b3b8e7e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346872"
---
# <a name="debugview-syntax"></a><span data-ttu-id="92733-103">`DebugView` syntaxe</span><span class="sxs-lookup"><span data-stu-id="92733-103">`DebugView` syntax</span></span>

<span data-ttu-id="92733-104">Vlastnost `DebugView` (k dispozici pouze při ladění) poskytuje řetězcové vykreslování stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="92733-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="92733-105">Většinu syntaxe je poměrně jasné pochopit; zvláštní případy jsou popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="92733-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="92733-106">Každý příklad následuje blok komentáře obsahující `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="92733-106">Each example is followed by a comment block containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="92733-107">Výraz ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="92733-107">ParameterExpression</span></span>

<span data-ttu-id="92733-108">názvy proměnných <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> jsou na začátku zobrazeny se symbolem "$".</span><span class="sxs-lookup"><span data-stu-id="92733-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="92733-109">Pokud parametr nemá název, je mu přiřazen automaticky generovaný název, například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="92733-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="92733-110">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-110">Examples</span></span>

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

## <a name="constantexpressions"></a><span data-ttu-id="92733-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="92733-111">ConstantExpressions</span></span>

<span data-ttu-id="92733-112">Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které reprezentují celočíselné hodnoty, řetězce a `null`, se zobrazí hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="92733-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="92733-113">Pro některé číselné typy je přípona přidána do hodnoty:</span><span class="sxs-lookup"><span data-stu-id="92733-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="92733-114">Typ</span><span class="sxs-lookup"><span data-stu-id="92733-114">Type</span></span> | <span data-ttu-id="92733-115">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="92733-115">Keyword</span></span> | <span data-ttu-id="92733-116">Auditování</span><span class="sxs-lookup"><span data-stu-id="92733-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="92733-117">UInteger –</span><span class="sxs-lookup"><span data-stu-id="92733-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="92733-118">U</span><span class="sxs-lookup"><span data-stu-id="92733-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="92733-119">Dlouhou</span><span class="sxs-lookup"><span data-stu-id="92733-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="92733-120">L</span><span class="sxs-lookup"><span data-stu-id="92733-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="92733-121">ULong</span><span class="sxs-lookup"><span data-stu-id="92733-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="92733-122">UL</span><span class="sxs-lookup"><span data-stu-id="92733-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="92733-123">Klepat</span><span class="sxs-lookup"><span data-stu-id="92733-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="92733-124">D</span><span class="sxs-lookup"><span data-stu-id="92733-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="92733-125">Konkrétní</span><span class="sxs-lookup"><span data-stu-id="92733-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="92733-126">Ž</span><span class="sxs-lookup"><span data-stu-id="92733-126">F</span></span> |
| <xref:System.Decimal> | [<span data-ttu-id="92733-127">Notaci</span><span class="sxs-lookup"><span data-stu-id="92733-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="92733-128">M</span><span class="sxs-lookup"><span data-stu-id="92733-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="92733-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-129">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="92733-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="92733-130">BlockExpression</span></span>

<span data-ttu-id="92733-131">Pokud se typ objektu <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> liší od typu posledního výrazu v bloku, zobrazí se typ v lomených závorkách (`<` a `>`).</span><span class="sxs-lookup"><span data-stu-id="92733-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="92733-132">V opačném případě není zobrazen typ objektu <xref:System.Linq.Expressions.BlockExpression>.</span><span class="sxs-lookup"><span data-stu-id="92733-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="92733-133">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-133">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="92733-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="92733-134">LambdaExpression</span></span>

<span data-ttu-id="92733-135">objekty <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> jsou zobrazovány spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="92733-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="92733-136">Pokud výraz lambda nemá název, je mu přiřazen automaticky generovaný název, například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="92733-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="92733-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-137">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="92733-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="92733-138">LabelExpression</span></span>

<span data-ttu-id="92733-139">Pokud zadáte výchozí hodnotu pro objekt <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, tato hodnota se zobrazí před objektem <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92733-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="92733-140">Token `.Label` označuje začátek popisku.</span><span class="sxs-lookup"><span data-stu-id="92733-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="92733-141">Token `.LabelTarget` označuje cíl cíle, na který se má přejít.</span><span class="sxs-lookup"><span data-stu-id="92733-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="92733-142">Pokud popisek nemá název, je mu přiřazen automaticky generovaný název, například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="92733-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="92733-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-143">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="92733-144">Kontrolované operátory</span><span class="sxs-lookup"><span data-stu-id="92733-144">Checked Operators</span></span>

<span data-ttu-id="92733-145">U zkontrolovaných operátorů se zobrazuje symbol `#` před operátorem.</span><span class="sxs-lookup"><span data-stu-id="92733-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="92733-146">Například operátor zaškrtnutí se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="92733-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="92733-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="92733-147">Examples</span></span>

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
