---
title: 'Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 04fe8b1add938f4e7aaa35e08d9924102c91cb9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721217"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView pomocí návrháře
Proces přidání položky do formulářů Windows <xref:System.Windows.Forms.ListView> ovládací prvek sestává především z zadáním položky a přiřazení vlastnosti k němu. Přidávání a odebírání položek seznamu lze provést kdykoli.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Chcete-li přidat nebo odebrat položky pomocí návrháře  
  
1.  Vyberte <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.ListView.Items%2A> vlastnost.  
  
     **Editor kolekce ListViewItem** se zobrazí.  
  
3.  Chcete-li přidat položku, klikněte na tlačítko **přidat** tlačítko. Potom můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListView.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.  
  
4.  Odebrat položku, vyberte ho a klikněte **odebrat** tlačítko.  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
