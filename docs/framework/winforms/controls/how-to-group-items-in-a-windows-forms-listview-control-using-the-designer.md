---
title: 'Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039403"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí Návrháře

Funkce <xref:System.Windows.Forms.ListView> seskupení ovládacího prvku umožňuje zobrazit související sady položek ve skupinách. Tyto skupiny jsou oddělené na obrazovce vodorovnými záhlavími skupin, která obsahují názvy skupin. Skupiny můžete použít <xref:System.Windows.Forms.ListView> k jednoduššímu procházení rozsáhlých seznamů tím, že položky seskupíte podle abecedy, podle data nebo do jiného logického seskupení. Následující obrázek ukazuje některé seskupené položky:

![Čísla rozdělená na liché a sudé skupiny.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

Chcete-li povolit seskupování, je nutné nejprve vytvořit jeden <xref:System.Windows.Forms.ListViewGroup> nebo více objektů buď v návrháři, nebo programově. Po definování skupiny můžete k ní přiřadit položky.

> [!NOTE]
> <xref:System.Windows.Forms.ListView>skupiny jsou k dispozici [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] pouze v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu. Ve starších operačních systémech žádný kód týkající se skupin nemá žádný vliv a skupiny se nezobrazí. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Přidání nebo odebrání skupin v Návrháři

1. V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.ListView.Groups%2A> .) vedle vlastnosti.

     Zobrazí se **Editor kolekce objektu ListView** .

2. Chcete-li přidat skupinu, klikněte na tlačítko **Přidat** . Pak můžete nastavit vlastnosti nové skupiny, například <xref:System.Windows.Forms.ListViewGroup.Header%2A> vlastnosti a. <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> Pokud chcete skupinu odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .

## <a name="to-assign-items-to-groups-in-the-designer"></a>Přiřazení položek do skupin v Návrháři

1. V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .) vedle vlastnosti.

     Zobrazí se **Editor kolekce ListViewItems** .

2. Chcete-li přidat novou položku, klikněte na tlačítko **Přidat** . Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListViewItem.Text%2A> vlastnosti a. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>

3. <xref:System.Windows.Forms.ListViewItem.Group%2A> Vyberte vlastnost a v rozevíracím seznamu vyberte skupinu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
