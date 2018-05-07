---
title: 'Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 83ea97b0961d158a1f3ab7a77ad2aa93732c17b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek může zobrazit více sloupců pro každý seznamu položky, když v **podrobnosti** zobrazení. Sloupce, které můžete použít k zobrazení několik typů informací o jednotlivých položkách seznamu. Seznam souborů, například může zobrazit, název souboru, typu souboru, velikost a datum poslední úpravy souboru. Informace o vyplnění sloupce po jejich vytvoření, najdete v části [postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku. Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-columns-in-the-designer"></a>Chcete-li přidat sloupce v Návrháři  
  
1.  V **vlastnosti** nastavte ovládacího prvku <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Details>.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **třemi tečkami** tlačítko (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ListView.Columns%2A> vlastnost.  
  
     **Editor kolekce ColumnHeader** se zobrazí.  
  
3.  Použití **přidat** tlačítko nové sloupce. Pak můžete vybrat na záhlaví sloupce a nastavit jeho text (titulek sloupec), zarovnání textu a šířkou.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
