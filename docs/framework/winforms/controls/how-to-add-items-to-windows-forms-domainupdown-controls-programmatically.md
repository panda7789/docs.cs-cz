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
ms.openlocfilehash: aaa6c58afa8dd39151f7e19890a6e933d82d049d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [DomainUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Přehled ovládacího prvku DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
