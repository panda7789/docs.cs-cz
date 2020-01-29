---
title: Seskupení položek v ovládacím prvku ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736679"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře

Funkce seskupení ovládacího prvku <xref:System.Windows.Forms.ListView> umožňuje zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin. Skupiny <xref:System.Windows.Forms.ListView> můžete použít k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení. Následující obrázek ukazuje některé seskupené položky:

![Čísla rozdělená na liché a sudé skupiny.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

Chcete-li povolit seskupování, je nutné nejprve vytvořit jeden nebo více <xref:System.Windows.Forms.ListViewGroup> objektů buď v návrháři, nebo programově. Po definování skupiny můžete k ní přiřadit položky.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Přidání nebo odebrání skupin v Návrháři

1. V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Groups%2A>.

     Zobrazí se **Editor kolekce objektu ListView** .

2. Chcete-li přidat skupinu, klikněte na tlačítko **Přidat** . Pak můžete nastavit vlastnosti nové skupiny, například <xref:System.Windows.Forms.ListViewGroup.Header%2A> a vlastnosti <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>. Pokud chcete skupinu odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Přiřazení položek do skupin v Návrháři

1. V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Items%2A>.

     Zobrazí se **Editor kolekce ListViewItems** .

2. Chcete-li přidat novou položku, klikněte na tlačítko **Přidat** . Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListViewItem.Text%2A> a vlastnosti <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.

3. Vyberte vlastnost <xref:System.Windows.Forms.ListViewItem.Group%2A> a v rozevíracím seznamu vyberte skupinu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
