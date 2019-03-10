---
title: 'Postupy: Změna zpoždění komponenty Windows Forms ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 5f3be7467aad8b14aa67dc57b8c23e585a62fa25
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704470"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Postupy: Změna zpoždění komponenty Windows Forms ToolTip
Existuje více hodnot zpoždění, které můžete nastavit pro Windows Forms <xref:System.Windows.Forms.ToolTip> komponenty. Jednotka měření pro všechny tyto vlastnosti je milisekund. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Vlastnost určuje, jak dlouho musí odkazovat uživatele na přidružený ovládací prvek pro řetězec popisku se zobrazí. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Vlastnost nastaví dobu v milisekundách, která je potřebná pro následující řetězce popis se zobrazí jako ukazatel myši přesune z jednoho ovládacího prvku ToolTip přidružené do jiného. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Vlastnost určuje dobu řetězec popisku se zobrazí. Tyto hodnoty můžete nastavit samostatně, nebo tak, že nastavíte hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost; zpoždění, které jsou nastaveny vlastnosti závislosti na hodnotě přiřazené k <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost. Například, když <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> je nastavena na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastavena na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastavena na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> rozdělené podle pět (nebo N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> je nastavena na hodnotu, která je pětkrát hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnosti (nebo 5N).  
  
### <a name="to-set-the-delay"></a>Chcete-li nastavit zpoždění  
  
1.  Jak je znázorněno v tomto příkladu, nastavte následující vlastnosti.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Přehled komponenty ToolTip](tooltip-component-overview-windows-forms.md)
- [Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Komponenta ToolTip](tooltip-component-windows-forms.md)
