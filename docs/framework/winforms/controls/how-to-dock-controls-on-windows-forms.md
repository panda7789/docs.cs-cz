---
title: 'Postupy: Ukotvování ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 82aef0ae9abacad33b21920f88591c0e4c33dfcb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460558"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Postupy: ukotvení ovládacích prvků na model Windows Forms

Můžete ukotvit ovládací prvky do okrajů formuláře nebo je nechat vyplnit kontejner ovládacího prvku (buď formuláře nebo ovládacího prvku kontejneru). Například Průzkumník Windows ukotví svůj <xref:System.Windows.Forms.TreeView> ovládací prvek na levou stranu okna a jeho <xref:System.Windows.Forms.ListView> ovládací prvek na pravou stranu okna. Pomocí vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> pro všechny viditelné ovládací prvky model Windows Forms definujte režim ukotvení.

> [!NOTE]
> Ovládací prvky jsou ukotveny v obráceném pořadí z.

Vlastnost <xref:System.Windows.Forms.Control.Dock%2A> komunikuje s vlastností <xref:System.Windows.Forms.Control.AutoSize%2A>. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Ukotvení ovládacího prvku

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.

2. V okně **vlastnosti** klikněte na šipku napravo od vlastnosti <xref:System.Windows.Forms.Control.Dock%2A>.

   Zobrazí se editor, který zobrazuje řadu polí reprezentujících okraje a střed formuláře.

3. Klikněte na tlačítko, které představuje okraj formuláře, kde chcete ovládací prvek ukotvit. Chcete-li vyplnit obsah formuláře ovládacího prvku nebo ovládacího prvku kontejneru, klikněte na středový rámeček. Chcete-li zakázat dokování, klikněte na tlačítko **(žádné)** .

   Velikost ovládacího prvku je automaticky nastavena tak, aby odpovídala hranicím ukotveného okraje.

   > [!NOTE]
   > Zděděné ovládací prvky musí být `Protected`, aby je bylo možné ukotvit. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho vlastnost **modifikátoru** v okně **vlastnosti** .

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
