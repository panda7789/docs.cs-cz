---
title: 'Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 0480c8980f0eba17229fff0c1e947cac5216fb9e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203435"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání a odebírání položek s ovládacím prvkem Windows Forms ListView pomocí Návrháře
Proces přidání položky do formulářů Windows <xref:System.Windows.Forms.ListView> ovládací prvek sestává především z zadáním položky a přiřazení vlastnosti k němu. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [postupy: vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Chcete-li přidat nebo odebrat položky pomocí návrháře  
  
1.  Vyberte <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     **Editor kolekce ListViewItem** se zobrazí.  
  
3.  Chcete-li přidat položku, klikněte na tlačítko **přidat** tlačítko. Potom můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListView.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.  
  
4.  Odebrat položku, vyberte ho a klikněte **odebrat** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
