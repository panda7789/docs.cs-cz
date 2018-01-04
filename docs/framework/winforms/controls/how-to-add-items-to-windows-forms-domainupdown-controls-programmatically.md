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
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="dc1d2-102">Postupy: Programové přidávání položek do ovládacích prvků Windows Forms DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dc1d2-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="dc1d2-103">Položky můžete přidat do Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek v kódu.</span><span class="sxs-lookup"><span data-stu-id="dc1d2-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="dc1d2-104">Volání <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třída k přidávání položek do ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1d2-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="dc1d2-105"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metoda přidá položku na konec kolekce, když <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda přidá položku na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="dc1d2-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="dc1d2-106">Chcete-li přidat novou položku</span><span class="sxs-lookup"><span data-stu-id="dc1d2-106">To add a new item</span></span>  
  
1.  <span data-ttu-id="dc1d2-107">Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> metody přidat položku na konec seznamu položek.</span><span class="sxs-lookup"><span data-stu-id="dc1d2-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="dc1d2-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dc1d2-108">-or-</span></span>  
  
2.  <span data-ttu-id="dc1d2-109">Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda vložení položky do seznamu na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="dc1d2-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc1d2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc1d2-110">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="dc1d2-111">Ovládací prvek DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dc1d2-111">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="dc1d2-112">Přehled ovládacího prvku DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dc1d2-112">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
