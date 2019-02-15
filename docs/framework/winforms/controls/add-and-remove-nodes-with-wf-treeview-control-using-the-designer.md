---
title: 'Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 3407b4636a9b9a6074a3721ee185504d8e6c0210
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304918"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView pomocí návrháře
Vzhledem k tomu, Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazuje uzly hierarchické způsobem, při přidávání uzlu musí věnovat pozornost na to, co je svého nadřazeného uzlu.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.TreeView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>K přidávání a odebírání uzlů v Návrháři  
  
1.  Vyberte <xref:System.Windows.Forms.TreeView> ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.  
  
     **TreeNode – Editor** se zobrazí.  
  
3.  Přidání uzlů, musí existovat kořenový uzel; Pokud neexistuje, musíte nejprve přidat kořenovou kliknutím **přidat kořenový** tlačítko. Potom můžete výběrem kořenové nebo druhý uzel a kliknutím na Přidat podřízené uzly **přidat podřízenou položku** tlačítko.  
  
4.  Odstranit uzly, vyberte uzel odstranit a potom klikněte na tlačítko **odstranit** tlačítko.  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
