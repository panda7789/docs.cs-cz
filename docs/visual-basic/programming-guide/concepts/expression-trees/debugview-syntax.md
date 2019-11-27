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
# <a name="debugview-syntax"></a>`DebugView` syntaxe

Vlastnost `DebugView` (k dispozici pouze při ladění) poskytuje řetězcové vykreslování stromů výrazů. Většinu syntaxe je poměrně jasné pochopit; zvláštní případy jsou popsány v následujících částech.

Každý příklad následuje blok komentáře obsahující `DebugView`.

## <a name="parameterexpression"></a>Výraz ParameterExpression

názvy proměnných <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> jsou na začátku zobrazeny se symbolem "$".

Pokud parametr nemá název, je mu přiřazen automaticky generovaný název, například `$var1` nebo `$var2`.

### <a name="examples"></a>Příklady

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

## <a name="constantexpressions"></a>ConstantExpressions

Pro <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objekty, které reprezentují celočíselné hodnoty, řetězce a `null`, se zobrazí hodnota konstanty.

Pro některé číselné typy je přípona přidána do hodnoty:

| Typ | Klíčové slovo | Auditování |
|--|--|--|
| <xref:System.UInt32> | [UInteger –](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Dlouhou](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Klepat](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Konkrétní](../../../language-reference/data-types/single-data-type.md) | Ž |
| <xref:System.Decimal> | [Notaci](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>Příklady

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

## <a name="blockexpression"></a>BlockExpression

Pokud se typ objektu <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> liší od typu posledního výrazu v bloku, zobrazí se typ v lomených závorkách (`<` a `>`). V opačném případě není zobrazen typ objektu <xref:System.Linq.Expressions.BlockExpression>.

### <a name="examples"></a>Příklady

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

## <a name="lambdaexpression"></a>LambdaExpression

objekty <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> jsou zobrazovány spolu s jejich typy delegátů.

Pokud výraz lambda nemá název, je mu přiřazen automaticky generovaný název, například `#Lambda1` nebo `#Lambda2`.

### <a name="examples"></a>Příklady

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

## <a name="labelexpression"></a>LabelExpression

Pokud zadáte výchozí hodnotu pro objekt <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, tato hodnota se zobrazí před objektem <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.

Token `.Label` označuje začátek popisku. Token `.LabelTarget` označuje cíl cíle, na který se má přejít.

Pokud popisek nemá název, je mu přiřazen automaticky generovaný název, například `#Label1` nebo `#Label2`.

### <a name="examples"></a>Příklady

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

## <a name="checked-operators"></a>Kontrolované operátory

U zkontrolovaných operátorů se zobrazuje symbol `#` před operátorem. Například operátor zaškrtnutí se zobrazí jako `#+`.

### <a name="examples"></a>Příklady

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
