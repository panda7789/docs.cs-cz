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
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="e785a-102">Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="e785a-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="e785a-103">Do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DomainUpDown> lze přidat položky v kódu.</span><span class="sxs-lookup"><span data-stu-id="e785a-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="e785a-104">Chcete-li přidat položky do vlastnosti <xref:System.Windows.Forms.DomainUpDown.Items%2A> ovládacího prvku, zavolejte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> třídy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>.</span><span class="sxs-lookup"><span data-stu-id="e785a-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="e785a-105">Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> přidá položku na konec kolekce, zatímco metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> přidá položku na určenou pozici.</span><span class="sxs-lookup"><span data-stu-id="e785a-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="e785a-106">Přidání nové položky</span><span class="sxs-lookup"><span data-stu-id="e785a-106">To add a new item</span></span>  
  
1. <span data-ttu-id="e785a-107">Chcete-li přidat položku na konec seznamu položek, použijte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="e785a-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="e785a-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e785a-108">-or-</span></span>  
  
2. <span data-ttu-id="e785a-109">Použijte metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> pro vložení položky do seznamu na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="e785a-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e785a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e785a-110">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e785a-111">Ovládací prvek DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="e785a-111">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="e785a-112">Přehled ovládacího prvku DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="e785a-112">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
