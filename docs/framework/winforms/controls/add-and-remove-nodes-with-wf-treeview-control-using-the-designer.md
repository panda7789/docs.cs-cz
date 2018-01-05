---
title: "Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6067302fd603b53ee075da837a29a3ebc05cc346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře
Protože Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazí uzly hierarchické uspořádání, při přidávání uzlu musí věnovat pozornost novinky svého nadřazeného uzlu.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.TreeView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Přidat nebo odebrat uzly v Návrháři  
  
1.  Vyberte <xref:System.Windows.Forms.TreeView> ovládacího prvku.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost.  
  
     **TreeNode Editor** se zobrazí.  
  
3.  Chcete-li přidat uzly, musí existovat kořenový uzel; Pokud žádný neexistuje, je nejprve nutno přidat kořenové kliknutím **přidat kořenový** tlačítko. Poté můžete výběrem kořenová CA nebo druhý uzel a kliknutím na Přidat podřízené uzly **přidat podřízenou** tlačítko.  
  
4.  Pokud chcete odstranit uzly, vyberte uzel odstranit a potom klikněte na **odstranit** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Přehled ovládacího prvku TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Postupy: Určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
