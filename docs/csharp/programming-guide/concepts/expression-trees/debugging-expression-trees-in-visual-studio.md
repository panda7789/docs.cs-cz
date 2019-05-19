---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877176"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v sadě Visual Studio (C#)
Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů. Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů pomocí speciální syntaxe popsané [níže](#debugview-syntax). (Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů:

* [Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, její vlastnosti a související objekty:

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Chcete-li otevřít vizualizér pro strom výrazu.  
  
1. Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.  
  
     Zobrazí seznam k dispozici vizualizéry.: 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Klikněte na vizualizaci, kterou chcete použít.  

## <a name="debugview-syntax"></a>`DebugView` Syntaxe 

Každý typ výrazu se zobrazí `DebugView` vlastnost, jak je popsáno v následujících částech.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.  
  
 Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.  
  
 Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona k hodnotě. V následující tabulce jsou uvedeny přípony spojené s různé číselné typy.  
  
|Type|Přípona|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >). V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.  
  
 Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.  
  
 `.Label` Token označuje začátek popisek. `.LabelTarget` Určuje cílové cíl, který chcete přejít na token.  
  
 Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Checked operátory  
 Checked operátory se zobrazí symbol "#" před operátor. Například operátor checked sčítání se zobrazí jako `#+`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Viz také:

- [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
