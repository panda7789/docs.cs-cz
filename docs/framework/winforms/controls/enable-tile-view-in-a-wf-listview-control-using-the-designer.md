---
title: Povolit zobrazení dlaždic v ovládacím prvku ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: a0429efaab14995ab1e3f3b0dfd91db61de72fbf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745801"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře
Funkce zobrazení dlaždice ovládacího prvku <xref:System.Windows.Forms.ListView> umožňuje zadat vizuální vyvážení mezi grafickými a textovými informacemi. Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností. Funkce zobrazení dlaždic v kombinaci s funkcemi seskupení nebo vložení v ovládacím prvku <xref:System.Windows.Forms.ListView>.

 V zobrazení dlaždice se používá ikona 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.

 ![Zobrazení dlaždic v ovládacím prvku ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Ikony a text dlaždicového zobrazení")

 Vlastnosti a metody zobrazení dlaždic umožňují určit, která sloupcová pole se mají zobrazit pro každou položku, a pro souhrnnou kontrolu velikosti a vzhledu všech položek v okně zobrazení dlaždic. Pro přehlednost je první řádek textu v dlaždici vždycky název položky; nedá se změnit.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-set-tile-view-in-the-designer"></a>Nastavení zobrazení dlaždic v Návrháři

1. V aplikaci Visual Studio vyberte ovládací prvek <xref:System.Windows.Forms.ListView> na formuláři.

2. V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.ListView.View%2A> a zvolte možnost **dlaždice**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
