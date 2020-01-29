---
title: Odebrání položek z ovládacích prvků DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735767"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown
Můžete odebrat položky z ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DomainUpDown> voláním metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> třídy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>. Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> odstraní konkrétní položku, zatímco metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> odstraní položku podle její pozice.  
  
### <a name="to-remove-an-item"></a>Odebrání položky  
  
- Pro odebrání položky podle názvu použijte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> třídy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     -nebo-  
  
- Pomocí metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> odeberte položku podle její pozice.  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [Ovládací prvek DomainUpDown](domainupdown-control-windows-forms.md)
- [Přehled ovládacího prvku DomainUpDown](domainupdown-control-overview-windows-forms.md)
