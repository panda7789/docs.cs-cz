---
title: 'Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 299b24eb42c576535389f53982581bf4a776ee3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource
Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vazbu ovládacího prvku Windows Forms ke zdroji dat může být nutné přizpůsobit vytvoření nové položky. <xref:System.Windows.Forms.BindingSource> Součást je tato možnost přehledné tím, že poskytuje <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která se obvykle vyvolá, když je potřeba vytvořit novou položku připojeného ovládacího prvku. Vaší obslužné rutiny událostí můžete zadat jakoukoli vlastní chování se vyžaduje (například volání metody na webové službě nebo získávání nový objekt ze třídy vytváření).  
  
> [!NOTE]
>  Když je položka přidána ve zpracování <xref:System.Windows.Forms.BindingSource.AddingNew> událostí, přidání nelze zrušit.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení pro vytváření třídy pomocí <xref:System.Windows.Forms.BindingSource> součásti. Když uživatel klikne <xref:System.Windows.Forms.DataGridView> ovládacího prvku nový řádek, <xref:System.Windows.Forms.BindingSource.AddingNew> událost se vyvolá. Vytvoří novou obslužnou rutinu události `DemoCustomer` objektu, která je přiřazená <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnost. To způsobí, že nové `DemoCustomer` objekt, který chcete přidat do <xref:System.Windows.Forms.BindingSource> seznamu součásti a který se má zobrazit na novém řádku z <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
