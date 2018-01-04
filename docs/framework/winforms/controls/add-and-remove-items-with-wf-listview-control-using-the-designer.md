---
title: "Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5000df10504c3dc0aad7950cdbe82fd53bc1c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře
Postup přidání položky do Windows Forms <xref:System.Windows.Forms.ListView> řízení se primárně skládá z zadáním položky a přiřazení vlastnosti k němu. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Přidat nebo odebrat položkami pomocí návrháře  
  
1.  Vyberte <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     **Editor kolekce ListViewItem** se zobrazí.  
  
3.  Chcete-li přidat položku, klikněte na tlačítko **přidat** tlačítko. Pak můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListView.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.  
  
4.  Chcete-li odebrat položku, vyberte ho a klikněte na tlačítko **odebrat** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
