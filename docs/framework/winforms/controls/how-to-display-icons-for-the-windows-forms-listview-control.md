---
title: 'Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 0e597ed182739947014b4f405ee2dc3149b62849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533601"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek může zobrazit ikony ze tří seznamů obrázků. Zobrazení seznamu, podrobnosti a SmallIcon zobrazení obrázků ze seznamu obrázků zadaný v <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost. Zobrazuje obrázků ze seznamu obrázků zadaný v zobrazení LargeIcon <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnost. Zobrazení seznamu lze také zobrazit další sadu ikony, nastavte v <xref:System.Windows.Forms.ListView.StateImageList%2A> vlastnost vedle velké nebo malé ikony. Další informace o seznamech obrázků najdete v tématu [ImageList – komponenta](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) a [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Pro zobrazení obrázků v zobrazení seznamu  
  
1.  Nastavte vlastnost odpovídající –<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, nebo <xref:System.Windows.Forms.ListView.StateImageList%2A>– ke stávající <xref:System.Windows.Forms.ImageList> součásti, které chcete použít.  
  
     Tyto vlastnosti můžete nastavit v návrháři se okno Vlastnosti, nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Nastavte <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> nebo <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> vlastnosti pro každou položku seznamu, který má přidružené ikonu.  
  
     Tyto vlastnosti lze nastavit v kódu nebo uvnitř **Editor kolekce ListViewItem**. Chcete-li otevřít **Editor kolekce ListViewItem**, klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.ListView.Items%2A>vlastnost **vlastnosti** okno.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Komponenta ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
