---
title: Programové přidávání položek do ovládacích prvků DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745591"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown
Do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DomainUpDown> lze přidat položky v kódu. Chcete-li přidat položky do vlastnosti <xref:System.Windows.Forms.DomainUpDown.Items%2A> ovládacího prvku, zavolejte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> třídy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>. Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> přidá položku na konec kolekce, zatímco metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> přidá položku na určenou pozici.  
  
### <a name="to-add-a-new-item"></a>Přidání nové položky  
  
1. Chcete-li přidat položku na konec seznamu položek, použijte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>.  
  
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
  
2. Použijte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> pro vložení položky do seznamu na zadané pozici.  
  
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
