---
title: 'Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 95e17675011b7e4d628b980fc0cbf15a50ce3932
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061270"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource
Pokud používáte ovládací prvky vázané na data, máte někdy reakce na změny ve zdroji dat, pokud zdroj dat události změny seznamu nevyvolá. Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby zdroje dat do ovládacího prvku Windows Forms, ovládací prvek, který se změnil zdroj dat voláním může upozornit <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> – metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metoda oznámení o aktualizaci ve zdroji dat vázaného ovládacího prvku.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
