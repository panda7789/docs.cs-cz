---
title: "Postupy: Implementace rozhraní INotifyPropertyChanged"
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
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="68440-102">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="68440-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="68440-103">Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68440-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="68440-104">Toto rozhraní implementujte na obchodní objekty, které se používají v systému Windows Forms – datová vazba.</span><span class="sxs-lookup"><span data-stu-id="68440-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="68440-105">Po implementaci rozhraní komunikuje připojeného ovládacího prvku změny vlastnost u objektu firmy.</span><span class="sxs-lookup"><span data-stu-id="68440-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68440-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="68440-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="68440-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="68440-107">See Also</span></span>  
 [<span data-ttu-id="68440-108">Postupy: použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="68440-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="68440-109">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="68440-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="68440-110">Postupy: vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged rozhraní</span><span class="sxs-lookup"><span data-stu-id="68440-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="68440-111">Oznámení změn v systému Windows Forms datové vazby</span><span class="sxs-lookup"><span data-stu-id="68440-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
