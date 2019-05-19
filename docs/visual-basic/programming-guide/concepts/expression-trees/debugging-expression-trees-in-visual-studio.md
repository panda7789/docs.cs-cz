---
title: Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879851"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů. Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů pomocí speciální syntaxe popsané [níže](#debugview-syntax). (Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů:

* [Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, vlastnosti a související objekty; a může mít za následek stromu výrazů kódu jazyka Visual Basic:

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Chcete-li otevřít vizualizér pro strom výrazu.  
  
1. Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.  
  
     Zobrazí seznam k dispozici vizualizéry.: 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Klikněte na vizualizaci, kterou chcete použít.  

## <a name="debugview-syntax"></a>`DebugView` Syntaxe 

Každý typ výrazu se zobrazí ve vizualizátoru, jak je popsáno v následujících částech.

## <a name="parameterexpressions"></a>ParameterExpressions

<xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.

Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    `DebugView` Vlastnost

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    `DebugView` Vlastnost

    `$var1`

## <a name="constantexpressions"></a>ConstantExpressions
 Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Vlastnost

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` Vlastnost

    10D

## <a name="blockexpression"></a>BlockExpression

Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >). V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    `DebugView` Vlastnost

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    `DebugView` Vlastnost

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.

Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    `DebugView` Vlastnost

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    `DebugView` Vlastnost

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.

`.Label` Token označuje začátek popisek. `.LabelTarget` Určuje cílové cíl, který chcete přejít na token.

Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    `DebugView` Vlastnost

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    `DebugView` Vlastnost

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>Checked operátory

Checked operátory se zobrazí symbol "#" před operátor. Například operátor checked sčítání se zobrazí jako `#+`.

### <a name="examples"></a>Příklady

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    `DebugView` Vlastnost

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    `DebugView` Vlastnost

    `#(System.Int32)10D`

## <a name="see-also"></a>Viz také:

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
