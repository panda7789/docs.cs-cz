---
title: 'Postupy: Ukotvování ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Postupy: Ukotvování ovládacích prvků ve Windows Forms
Můžete ukotvení ovládací prvky hrany svého formuláře nebo kliknul vyplnění kontejneru ovládacího prvku (formuláře nebo ovládacího prvku kontejneru). Například Průzkumník Windows ukotvené jeho <xref:System.Windows.Forms.TreeView> ovládacího prvku na levé straně okna a jeho <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně okna. Použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost pro všechny viditelné ovládací prvky Windows Forms k definování ukotvení režimu.  
  
> [!NOTE]
>  Ovládací prvky jsou ukotven v obráceném pořadí z.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje s <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Chcete-li ukotvit ovládacího prvku  
  
1.  Vyberte ovládací prvek, který chcete ukotvit.  
  
2.  V okně vlastností klikněte na šipku napravo <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.  
  
     Editor se zobrazí, které zobrazuje sérii polí představující hrany a střed tvaru.  
  
3.  Klikněte na tlačítko, který představuje hrany formuláře, které chcete ukotvit ovládacího prvku. K vyplnění obsah ovládacího prvku formuláře nebo ovládacího prvku kontejneru, klikněte na políčko center. Klikněte na tlačítko **(none)** zakázat ukotvení.  
  
     Ovládací prvek automaticky se přizpůsobí hranice ukotveného okraj.  
  
    > [!NOTE]
    >  Musí být zděděné ovládací prvky `Protected` moct ukotvit. Chcete-li změnit úroveň přístupu tohoto ovládacího prvku, nastavte jeho **modifikátor** vlastnost v okně Vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Postupy: Ukotvení ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
