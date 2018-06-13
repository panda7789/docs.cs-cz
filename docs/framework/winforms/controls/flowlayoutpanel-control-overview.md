---
title: FlowLayoutPanel – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526722"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel – přehled ovládacího prvku
<xref:System.Windows.Forms.FlowLayoutPanel> Řízení uspořádá jeho obsah v směr toku vodorovně nebo svisle. Může obtékat obsah ovládacího prvku z jeden řádek na další, nebo z jednoho sloupce na další. Místo wrap můžete alternativně oříznutí její obsah.  
  
 Směr toku můžete zadat nastavení hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost. <xref:System.Windows.Forms.FlowLayoutPanel> Řízení správně obrátí jeho směr toku v rozložení doleva (RTL). Můžete také určit, zda <xref:System.Windows.Forms.FlowLayoutPanel> obsah ovládacího prvku zalomen nebo oříznut podle nastavení hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Řídit automaticky velikosti k jejímu obsahu při nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`. Poskytuje také **FlowBreak** vlastnosti tak, aby jeho podřízených ovládacích prvků. Nastavení hodnoty vlastnosti FlowBreak `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> řízení zastavit rozložení ovládacích prvků v aktuální směr toku a wrap na další řádek nebo sloupec.  
  
 Libovolný ovládací prvek Windows Forms může být podřízená <xref:System.Windows.Forms.FlowLayoutPanel> řízení, včetně ostatní instance <xref:System.Windows.Forms.FlowLayoutPanel>. Díky této funkci můžete vytvořit sofistikované rozložení, které přizpůsobit do svého formuláře dimenzí v době běhu.  
  
 Viz také [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Ovládací prvek FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
