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
ms.openlocfilehash: 8e4ae744eecbe894767114179dd63651828b191b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013436"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek mohl zobrazit ikony ze tří seznamů obrázků. Zobrazení seznamu, podrobnosti a SmallIcon zobrazit obrázky ze zadaného v seznamu obrázků <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost. Zobrazení LargeIcon zobrazuje obrázky ze zadaného v seznamu obrázků <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnost. Zobrazení seznamu můžete také zobrazit další sadu ikon, nastavte <xref:System.Windows.Forms.ListView.StateImageList%2A> vlastnost vedle velké nebo malé ikony. Další informace o seznamech image, najdete v části [komponenty ImageList](imagelist-component-windows-forms.md) a [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Chcete-li zobrazit obrázky v zobrazení seznamu  
  
1. Nastavit vlastnost odpovídající –<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, nebo <xref:System.Windows.Forms.ListView.StateImageList%2A>– ke stávající <xref:System.Windows.Forms.ImageList> komponenty, které chcete použít.  
  
     Tyto vlastnosti můžete nastavit v návrháři se v okně Vlastnosti, nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Nastavte <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> nebo <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> vlastností pro každou položku seznamu, která má související ikony.  
  
     Tyto vlastnosti lze nastavit v kódu nebo v rámci **Editor kolekce ListViewItem**. Chcete-li otevřít **Editor kolekce ListViewItem**, klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.ListView.Items%2A>vlastnost **vlastnosti** okna.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
