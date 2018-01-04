---
title: "Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown"
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
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e540e394226f20c40915f4d9de31afcffdf6e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown
Položky můžete přidat do Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek v kódu. Volání <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třída k přidávání položek do ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.Items%2A> vlastnost. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metoda přidá položku na konec kolekce, když <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda přidá položku na zadané pozici.  
  
### <a name="to-add-a-new-item"></a>Chcete-li přidat novou položku  
  
1.  Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> metody přidat položku na konec seznamu položek.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     -nebo-  
  
2.  Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda vložení položky do seznamu na zadané pozici.  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [Ovládací prvek DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Přehled ovládacího prvku DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
