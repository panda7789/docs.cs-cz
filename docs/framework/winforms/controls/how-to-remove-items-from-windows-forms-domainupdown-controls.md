---
title: "Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown"
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
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cab9bf4445c7322c1b4824f26c0821de8c58657
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown
Můžete odebrat položky z rozhraní Windows Forms <xref:System.Windows.Forms.DomainUpDown> řízení voláním <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třídy. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda odebere určitou položku, zatímco <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda odebere položku podle jeho umístění.  
  
### <a name="to-remove-an-item"></a>Pokud chcete odebrat položku  
  
-   Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třídy pro odebrání položky podle názvu.  
  
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
  
-   Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda pro odebrání položky podle jeho umístění.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [DomainUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Přehled ovládacího prvku DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
