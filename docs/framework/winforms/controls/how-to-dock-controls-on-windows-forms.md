---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987487"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Postupy: Ukotvit ovládací prvky na model Windows Forms

Můžete ukotvit ovládací prvky do okrajů formuláře nebo je nechat vyplnit kontejner ovládacího prvku (buď formuláře nebo ovládacího prvku kontejneru). Například Průzkumník Windows ukotví svůj <xref:System.Windows.Forms.TreeView> ovládací prvek na levou stranu okna a jeho <xref:System.Windows.Forms.ListView> ovládací prvek na pravou stranu okna. <xref:System.Windows.Forms.Control.Dock%2A> Pomocí vlastnosti pro všechny viditelné model Windows Forms ovládací prvky definujte režim ukotvení.

> [!NOTE]
> Ovládací prvky jsou ukotveny v obráceném pořadí z.

<xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje<xref:System.Windows.Forms.Control.AutoSize%2A> s vlastností. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Ukotvení ovládacího prvku

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.

2. V okně **vlastnosti** klikněte na šipku napravo od <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.

   Zobrazí se editor, který zobrazuje řadu polí reprezentujících okraje a střed formuláře.

3. Klikněte na tlačítko, které představuje okraj formuláře, kde chcete ovládací prvek ukotvit. Chcete-li vyplnit obsah formuláře ovládacího prvku nebo ovládacího prvku kontejneru, klikněte na středový rámeček. Chcete-li zakázat dokování, klikněte na tlačítko **(žádné)** .

   Velikost ovládacího prvku je automaticky nastavena tak, aby odpovídala hranicím ukotveného okraje.

   > [!NOTE]
   > Zděděné ovládací prvky `Protected` musí být schopny být ukotveny. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho vlastnost modifikátoru v okně **vlastnosti** .

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ovládací prvky ukotvení na model Windows Forms](how-to-anchor-controls-on-windows-forms.md)
