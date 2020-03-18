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
# <a name="debugview-syntax"></a>`DebugView`Syntaxe

Vlastnost `DebugView` (k dispozici pouze při ladění) poskytuje vykreslování řetězce stromů výrazů. Většina syntaxe je poměrně jednoduché pochopit; zvláštní případy jsou popsány v následujících oddílech.

Za každým příkladem následuje blokový komentář `DebugView`obsahující .

## <a name="parameterexpression"></a>Parameterexpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>názvy proměnných jsou `$` zobrazeny se symbolem na začátku.

Pokud parametr nemá název, je mu přiřazen automaticky generovaný `$var1` `$var2`název, například nebo .

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

## <a name="constantexpression"></a>Constantexpression

Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které představují celé hodnoty, řetězce a `null`, je zobrazena hodnota konstanty.

Pro číselné typy, které mají standardní přípony jako literály jazyka C#, je přípona přidána k hodnotě. V následující tabulce jsou uvedeny přípony přidružené k různým číselným typům.

| Typ | Klíčové slovo | Přípona |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/builtin-types/integral-numeric-types.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/builtin-types/integral-numeric-types.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/builtin-types/integral-numeric-types.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/builtin-types/floating-point-numeric-types.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/builtin-types/floating-point-numeric-types.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/builtin-types/floating-point-numeric-types.md) | M |

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

## <a name="blockexpression"></a>Blockexpression

Pokud se typ <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objektu liší od typu posledního výrazu v bloku, zobrazí se`<` `>`text v rámci úhlových závorek ( a ). V opačném případě <xref:System.Linq.Expressions.BlockExpression> se nezobrazí typ objektu.

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

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>objekty jsou zobrazeny společně s jejich typy delegátů.

Pokud výraz lambda nemá název, je mu přiřazen automaticky generovaný název, například `#Lambda1` nebo `#Lambda2`.

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

Pokud zadáte výchozí hodnotu <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> objektu, tato hodnota <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> se zobrazí před objektem.

Token `.Label` označuje začátek popisku. Token `.LabelTarget` označuje cíl cíle, na který chcete přejít.

Pokud popisek nemá název, je mu přiřazen automaticky generovaný název, například `#Label1` nebo `#Label2`.

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

## <a name="checked-operators"></a>Kontrolované operátory

Kontrolované operátory jsou zobrazeny se symbolem `#` před operátorem. Například operátor checked sčítání se `#+`zobrazí jako .

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
