---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941492"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Postupy: Ukotvení ovládacích prvků ve Windows Forms
Můžete ukotvit ovládací prvky k okrajům formuláře nebo ho zadejte kontejneru ovládacího prvku (formuláře nebo ovládací prvek kontejneru). Například Windows Explorer ukotvené jeho <xref:System.Windows.Forms.TreeView> ovládacího prvku na levé straně okna a jeho <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně okna. Použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti pro všechny viditelné prvky Windows Forms k definování dokovací režimu.  
  
> [!NOTE]
>  Ovládací prvky jsou ukotveny v obráceném pořadí vykreslování.  
  
 <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Další informace najdete v tématu [přehled vlastnosti AutoSize](autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Chcete-li ukotvit ovládacího prvku  
  
1. Vyberte ovládací prvek, který chcete ukotvit.  
  
2. V okně Vlastnosti klikněte na šipku vpravo od <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.  
  
     Editoru se zobrazí, který zobrazuje řadu polí představující hrany a střed formuláře.  
  
3. Klikněte na tlačítko, který představuje edge formuláře, ve které chcete ukotvit ovládacího prvku. K vyplnění obsah ovládacího prvku formulář nebo ovládací prvek kontejneru, klikněte na tlačítko prostředním poli. Klikněte na tlačítko **(žádný)** zakázat ukotvení.  
  
     Ovládací prvek automaticky se přizpůsobí hranice ukotvených edge.  
  
    > [!NOTE]
    >  Zděděný ovládací prvky musí být `Protected` lze ukotvit. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho **modifikátor** vlastností v okně Vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
