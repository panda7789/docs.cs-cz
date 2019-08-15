---
title: 'Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040355"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView pomocí Návrháře
Funkce zobrazení dlaždice <xref:System.Windows.Forms.ListView> ovládacího prvku umožňuje zadat vizuální vyvážení mezi grafickými a textovými informacemi. Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností. Funkce zobrazení dlaždic v kombinaci s funkcemi seskupení nebo vložení v <xref:System.Windows.Forms.ListView> ovládacím prvku

 V zobrazení dlaždice se používá ikona 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.

 ![Zobrazení dlaždic v ovládacím prvku ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Ikony a text dlaždicového zobrazení")

 Vlastnosti a metody zobrazení dlaždic umožňují určit, která sloupcová pole se mají zobrazit pro každou položku, a pro souhrnnou kontrolu velikosti a vzhledu všech položek v okně zobrazení dlaždic. Pro přehlednost je první řádek textu v dlaždici vždycky název položky; nedá se změnit.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

> [!NOTE]
> Zobrazení dlaždice je k dispozici pouze [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] v případě, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> že vaše aplikace volá metodu. V předchozích operačních systémech nemá žádný vliv žádný kód související s zobrazením dlaždice a <xref:System.Windows.Forms.ListView> ovládací prvek se zobrazí v zobrazení velkých ikon. Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.

## <a name="to-set-tile-view-in-the-designer"></a>Nastavení zobrazení dlaždic v Návrháři

1. V aplikaci Visual Studio vyberte <xref:System.Windows.Forms.ListView> ovládací prvek ve formuláři.

2. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.ListView.View%2A> vlastnost a zvolte možnost **dlaždice**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
