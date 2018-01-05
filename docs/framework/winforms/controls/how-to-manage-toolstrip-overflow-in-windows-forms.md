---
title: "Postupy: Správa přetečení ToolStrip ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 619c4832626693a56280c70af3ade5dbb9e9d4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Postupy: Správa přetečení ToolStrip ve Windows Forms
Pokud všechny položky v <xref:System.Windows.Forms.ToolStrip> ovládacího prvku nelze uložit do přidělené místo, můžete povolit funkce přetečení na <xref:System.Windows.Forms.ToolStrip> a určují chování přetečení konkrétní <xref:System.Windows.Forms.ToolStripItem>s.  
  
 Když přidáte <xref:System.Windows.Forms.ToolStripItem>s, která vyžadují víc místa, než je vymezena pro <xref:System.Windows.Forms.ToolStrip> danou aktuální velikost formuláře, <xref:System.Windows.Forms.ToolStripOverflowButton> automaticky se zobrazí na <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Se zobrazí, a položek s povolenou přetečení přesunou do nabídky přetečení rozevíracího seznamu. To umožňuje přizpůsobit a určit jejich prioritu jak vaše <xref:System.Windows.Forms.ToolStrip> položky správně upravit pro různé typy velikosti. Můžete také změnit vzhled položek, jsou-li do oblasti přetečení pomocí <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí. V případě více zvětšení formuláře v době návrhu nebo běhu <xref:System.Windows.Forms.ToolStripItem>s lze zobrazit v hlavním <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripOverflowButton> může zmizet i, dokud snížit velikost formuláře.  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>Chcete-li povolit přetečení na ovládacího prvku ToolStrip  
  
-   Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>. Výchozí hodnota je `True`.  
  
     Při <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> je `True` (výchozí), <xref:System.Windows.Forms.ToolStripItem> je odeslána do nabídky rozevíracího seznamu přetečení při obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířka vodorovného <xref:System.Windows.Forms.ToolStrip> nebo výšky svislého <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>K určení chování přetečení konkrétní ToolStripItem  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu. Možnosti jsou `Always`, `Never`, a `AsNeeded`. Defaultis `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
