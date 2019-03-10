---
title: 'Postupy: Programové přidání položek do ovládacích prvků Windows Forms DomainUpDown'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 06c2c83ddfba67aaff775065cc2aa4515978bf81
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722708"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Postupy: Programové přidání položek do ovládacích prvků Windows Forms DomainUpDown
Můžete přidat položky do formulářů Windows <xref:System.Windows.Forms.DomainUpDown> ovládacího prvku v kódu. Volání <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třídy k přidání položek do ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.Items%2A> vlastnost. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metoda přidá položku na konec kolekce, zatímco <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda přidá položku na určené pozici.  
  
### <a name="to-add-a-new-item"></a>Chcete-li přidat novou položku  
  
1.  Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> způsob, jak přidat položku na konec seznamu položek.  
  
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
  
2.  Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodu pro vložení položky do seznamu na zadané pozici.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [Ovládací prvek DomainUpDown](domainupdown-control-windows-forms.md)
- [Přehled ovládacího prvku DomainUpDown](domainupdown-control-overview-windows-forms.md)
