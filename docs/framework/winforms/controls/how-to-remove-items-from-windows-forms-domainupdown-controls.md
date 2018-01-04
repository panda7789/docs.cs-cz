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
ms.workload: dotnet
ms.openlocfilehash: 17972aa9cb1626793ab04d317bb66d2774899cfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="dcadd-102">Postupy: Odebrání položek z ovládacích prvků Windows Forms DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dcadd-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="dcadd-103">Můžete odebrat položky z rozhraní Windows Forms <xref:System.Windows.Forms.DomainUpDown> řízení voláním <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="dcadd-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="dcadd-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda odebere určitou položku, zatímco <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda odebere položku podle jeho umístění.</span><span class="sxs-lookup"><span data-stu-id="dcadd-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="dcadd-105">Pokud chcete odebrat položku</span><span class="sxs-lookup"><span data-stu-id="dcadd-105">To remove an item</span></span>  
  
-   <span data-ttu-id="dcadd-106">Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metodu <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> třídy pro odebrání položky podle názvu.</span><span class="sxs-lookup"><span data-stu-id="dcadd-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="dcadd-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dcadd-107">-or-</span></span>  
  
-   <span data-ttu-id="dcadd-108">Použití <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda pro odebrání položky podle jeho umístění.</span><span class="sxs-lookup"><span data-stu-id="dcadd-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcadd-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcadd-109">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="dcadd-110">Ovládací prvek DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dcadd-110">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="dcadd-111">Přehled ovládacího prvku DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dcadd-111">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
