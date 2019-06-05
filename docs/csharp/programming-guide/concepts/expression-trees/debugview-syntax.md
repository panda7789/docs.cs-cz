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
# <a name="debugview-syntax"></a>`DebugView` Syntaxe

`DebugView` (K dispozici pouze při ladění) obsahuje řetězec vykreslování stromů výrazů. Většina syntaxe je celkem jasné, abyste pochopili; zvláštní případy jsou popsány v následujících částech.

Každý příklad následuje blok komentáře, který obsahuje `DebugView`.

## <a name="parameterexpression"></a>Výraz ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> se zobrazují názvy proměnných `$` symbolu na počátku.

Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.

### <a name="examples"></a>Příklady

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

## <a name="constantexpression"></a>ConstantExpression

Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.

Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona k hodnotě. V následující tabulce jsou uvedeny přípony spojené s různé číselné typy.

| Type | Klíčové slovo | Přípona |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/keywords/uint.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/keywords/long.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/keywords/ulong.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/keywords/double.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/keywords/float.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/keywords/decimal.md) | M |

### <a name="examples"></a>Příklady

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

## <a name="blockexpression"></a>BlockExpression

Pokud typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objektu se liší od typu posledního výrazu v bloku, zobrazí se typ v lomených závorkách (`<` a `>`). V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.

### <a name="examples"></a>Příklady

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

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objekty se zobrazí spolu s jejich typy delegátů.

Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.

### <a name="examples"></a>Příklady

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

## <a name="labelexpression"></a>LabelExpression

Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> objektu.

`.Label` Token označuje začátek popisek. `.LabelTarget` Určuje cílové cíl, který chcete přejít na token.

Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.

### <a name="examples"></a>Příklady

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

## <a name="checked-operators"></a>Checked operátory

Checked operátory jsou zobrazovány `#` symbol před operátor. Například operátor checked sčítání se zobrazí jako `#+`.

### <a name="examples"></a>Příklady

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
