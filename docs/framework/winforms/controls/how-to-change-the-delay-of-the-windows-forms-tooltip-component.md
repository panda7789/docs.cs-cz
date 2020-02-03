---
title: Změna zpoždění součásti ToolTip
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746585"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Postupy: Změna zpoždění součásti Windows Forms ToolTip
Existuje více hodnot zpoždění, které lze nastavit pro komponentu model Windows Forms <xref:System.Windows.Forms.ToolTip>. Jednotka měření všech těchto vlastností je milisekund. Vlastnost <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> určuje, jak dlouho musí uživatel ukazovat na přidružený ovládací prvek, aby se zobrazil řetězec s popisem tlačítka. Vlastnost <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> nastaví počet milisekund, které bude trvat, než se při přesunutí ukazatele myši z jednoho ovládacího prvku přidruženého k popisku na jiný ovládací prvek s popisem tlačítka zobrazí v milisekundách. Vlastnost <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> určuje dobu, po kterou je zobrazen řetězec s popisem tlačítka. Tyto hodnoty můžete nastavit individuálně nebo nastavením hodnoty vlastnosti <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; Ostatní vlastnosti zpoždění jsou nastaveny na základě hodnoty přiřazené vlastnosti <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>. Pokud je například <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> nastaveno na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastavena na hodnotu N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastavena na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dělenou pěti (nebo N/5) a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> je nastavena na hodnotu, která je pětkrát hodnotou <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnosti (nebo 5N).  
  
### <a name="to-set-the-delay"></a>Nastavení zpoždění  
  
1. Nastavte následující vlastnosti, jak je znázorněno v tomto příkladu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled komponenty ToolTip](tooltip-component-overview-windows-forms.md)
- [Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Komponenta ToolTip](tooltip-component-windows-forms.md)
