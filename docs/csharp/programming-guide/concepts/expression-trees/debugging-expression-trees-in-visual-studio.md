---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702994"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v sadě Visual Studio (C#)
Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů. Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění. Další informace o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Pro lepší reprezentaci obsah stromů výrazů `DebugView` vlastnost používá Visual Studio vizualizéry. Další informace najdete v tématu [vytvořit vlastní Vizualizéry](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Chcete-li otevřít vizualizér pro strom výrazu.  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle `DebugView` vlastnost strom výrazu v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **Lokální** okna.  
  
     Zobrazí se seznam vizualizéry.  
  
2. Klikněte na vizualizaci, kterou chcete použít.  
  
 Každý typ výrazu se zobrazí ve vizualizátoru, jak je popsáno v následujících částech.  
  
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
