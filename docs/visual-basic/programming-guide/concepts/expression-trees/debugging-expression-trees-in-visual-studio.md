---
title: Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2addba2654067eaaf6c621c927e0992308879ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
Při ladění aplikace můžete analyzovat struktuře a obsahu stromů výrazů. Chcete-li získat rychlý přehled o výraz stromová struktura, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění. Další informace o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Lépe představují obsah stromů výrazů `DebugView` vlastnost používá vizualizérech Visual Studio. Další informace najdete v tématu [vytvořit vlastní Vizualizérech](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Chcete-li otevřít vizualizér pro strom výrazu se nezdařilo  
  
1.  Klikněte na ikonu lupy, který se zobrazí vedle `DebugView` vlastnost strom výrazu v **datatips –**, **sledovat** okně **automobily** okno, nebo **Místní hodnoty –** okno.  
  
     Zobrazí se seznam vizualizérech.  
  
2.  Klikněte na tlačítko vizualizér, kterou chcete použít.  
  
 Každý typ výrazu se zobrazí v vizualizér, jak je popsáno v následujících částech.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny symbolem "$" na začátku.  
  
 Pokud parametr nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `$var1` nebo `$var2`.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView` Vlastnost  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView` Vlastnost  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselné hodnoty řetězce, a `null`, zobrazí se hodnota konstanty.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` Vlastnost  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` Vlastnost  
  
     10D  
  
## <a name="blockexpression"></a>BlockExpression  
 Pokud se typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typ poslední výrazu v bloku, typ se zobrazí v `DebugInfo` vlastnost v lomených závorkách (\< a >). Jinak typ <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazí.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView` Vlastnost  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView` Vlastnost  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> Zobrazí se objekty, spolu s jejich typů delegátů.  
  
 Pokud výrazu lambda nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Lambda1` nebo `#Lambda2`.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView` Vlastnost  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView` Vlastnost  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 Pokud zadáte výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, tato hodnota se zobrazí před <xref:System.Linq.Expressions.LabelTarget> objektu.  
  
 `.Label` Token označuje začátek popisku. `.LabelTarget` Token označuje cílovým serverem cíl, který má přejít na.  
  
 Pokud štítek nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Label1` nebo `#Label2`.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
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
  
-   `Expression`  
  
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
 Checked operátory se zobrazí symbol "#" před operátor. Např. operátor sčítání zaškrtnuté je zobrazen jako `#+`.  
  
### <a name="examples"></a>Příklady  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     `DebugView` Vlastnost  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView` Vlastnost  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Viz také  
 [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Vytvořit vlastní Vizualizérech](/visualstudio/debugger/create-custom-visualizers-of-data)
