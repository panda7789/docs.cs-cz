---
title: "Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5c2fb155508ca2a86dbc5e63caabb25be71bcfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a>Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource
Pokud používáte ovládací prvky vázané na data, máte někdy odpověď na změny ve zdroji dat, pokud zdroj dat není vyvolávání událostí seznam změnil. Při použití <xref:System.Windows.Forms.BindingSource> součást k vytvoření vazby zdroje dat do ovládacího prvku Windows Forms uvědomí ovládací prvek, který zdroje dat došlo ke změně voláním <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metoda oznámení o aktualizaci ve zdroji dat připojeného ovládacího prvku.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
