---
title: "Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25b0dc81a6511698394eb86343f09051befc87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře
Při vytváření ovládacích prvků, které pracují s daty, někdy potřebujete k vytvoření vazby ovládacího prvku typu, nikoli objekt. Obvykle je nutné vytvořit vazbu ovládacího prvku typu v době návrhu, když data nemusí být k dispozici, ale stále chcete vaše ovládací prvky vázané na data k zobrazení dat z veřejné rozhraní typu. Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> který je vázaný na typ a poté jak pro některé vlastnosti typu na vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>Pro vazbu na typ BindingSource  
  
1.  Vytvořte projekt Windows Forms.  
  
     Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  V **návrhu** zobrazení, přetáhněte ji <xref:System.Windows.Forms.BindingSource> součásti do formuláře.  
  
3.  V **vlastnosti** okně klikněte na šipku u položky <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.  
  
4.  V **Editor typů uživatelského rozhraní pro zdroj dat**, klikněte na tlačítko **přidat zdroj dat projektu**.  
  
5.  Na **zvolte typ zdroje dat** vyberte **objekt** a klikněte na tlačítko **Další**.  
  
6.  Vyberte typ k vytvoření vazby:  
  
    -   Pokud v aktuálním projektu, které chcete vytvořit vazbu na typ nebo sestavení, které obsahuje typ je již přidána jako odkaz, rozbalte uzly se najít typ, který má být a pak ho vyberte.  
  
         -nebo-  
  
    -   Pokud chcete vytvořit vazbu na typ je v jiném sestavení není aktuálně v seznamu odkazů na, klikněte na tlačítko **přidat odkaz na**a klikněte **projekty** kartě. Vyberte projekt, který obsahuje objekt obchodní a klikněte na tlačítko **OK**. Tento projekt se objeví v seznamu sestavení, tak můžete rozbalit uzly se najít typ můžete má a pak ho vyberte.  
  
        > [!NOTE]
        >  Pokud chcete vytvořit vazbu na typ v framework nebo Microsoft sestavení, zrušte **skrýt sestavení, které začínají s Microsoftem nebo systému** zaškrtávací políčko.  
  
7.  Klikněte na tlačítko **Další**a potom klikněte na **Dokončit**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>K vytvoření vazby ovládacího prvku BindingSource  
  
1.  Přidat <xref:System.Windows.Forms.TextBox> do formuláře.  
  
2.  V **vlastnosti** okno, rozbalte **(datové vazby)** uzlu.  
  
3.  Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
4.  V **Editor typů uživatelského rozhraní pro zdroj dat**, rozbalte uzel <xref:System.Windows.Forms.BindingSource> přidali dříve a vyberte vlastnost typu vázané chcete vytvořit vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Viz také  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
