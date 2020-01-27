---
title: Zobrazit ikony pro ovládací prvek ListView
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
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744504"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> může zobrazit ikony ze tří seznamů obrázků. Zobrazení seznam, podrobnosti a SmallIcon zobrazují obrázky ze seznamu obrázků zadaného ve vlastnosti <xref:System.Windows.Forms.ListView.SmallImageList%2A>. Zobrazení zobrazení LargeIcon zobrazí obrázky ze seznamu obrázků zadaného ve vlastnosti <xref:System.Windows.Forms.ListView.LargeImageList%2A>. Zobrazení seznamu může také zobrazit další sadu ikon, nastavit vlastnost <xref:System.Windows.Forms.ListView.StateImageList%2A> vedle velkých nebo malých ikon. Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [Postupy: Přidání nebo odebrání obrázků s komponentou model Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Zobrazení obrázků v zobrazení seznamu  
  
1. Nastavte odpovídající vlastnost –<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>nebo <xref:System.Windows.Forms.ListView.StateImageList%2A>– na stávající komponentu <xref:System.Windows.Forms.ImageList>, kterou chcete použít.  
  
     Tyto vlastnosti lze nastavit v Návrháři pomocí okno Vlastnosti nebo v kódu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Pro každou položku seznamu, která má přidruženou ikonu, nastavte vlastnost <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> nebo <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>.  
  
     Tyto vlastnosti lze nastavit v kódu nebo v **editoru kolekce ListViewItem**. Chcete-li otevřít **Editor kolekce ListViewItem**, klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Items%2A> v okně **vlastnosti** .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
