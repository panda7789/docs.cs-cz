---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 0b3017f2800a2eb7332028b9cfe6ed9877222087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v sadě Visual Studio (C#)
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
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselné hodnoty řetězce, a `null`, zobrazí se hodnota konstanty.  
  
 Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona hodnotě. V následující tabulce jsou uvedeny přípony spojené s různými číselnými typy.  
  
|Typ|Přípona|  
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
 Pokud se typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typ poslední výrazu v bloku, typ se zobrazí v `DebugInfo` vlastnost v lomených závorkách (\< a >). Jinak typ <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazí.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> Zobrazí se objekty, spolu s jejich typů delegátů.  
  
 Pokud výrazu lambda nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Lambda1` nebo `#Lambda2`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Pokud zadáte výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, tato hodnota se zobrazí před <xref:System.Linq.Expressions.LabelTarget> objektu.  
  
 `.Label` Token označuje začátek popisku. `.LabelTarget` Token označuje cílovým serverem cíl, který má přejít na.  
  
 Pokud štítek nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Label1` nebo `#Label2`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Checked operátory  
 Checked operátory se zobrazí symbol "#" před operátor. Např. operátor sčítání zaškrtnuté je zobrazen jako `#+`.  
  
### <a name="examples"></a>Příklady  
  
|Výraz|`DebugView` Vlastnost|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Viz také  
 [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Vytvořit vlastní Vizualizérech](/visualstudio/debugger/create-custom-visualizers-of-data)
