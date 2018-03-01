---
title: "Postupy: Implementace rozhraní INotifyPropertyChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ded5d11c9a9f93848e17c372e961f9f6a3b4226
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="4b945-102">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="4b945-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="4b945-103">Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4b945-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="4b945-104">Toto rozhraní implementujte na obchodní objekty, které se používají v systému Windows Forms – datová vazba.</span><span class="sxs-lookup"><span data-stu-id="4b945-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="4b945-105">Po implementaci rozhraní komunikuje připojeného ovládacího prvku změny vlastnost u objektu firmy.</span><span class="sxs-lookup"><span data-stu-id="4b945-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b945-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b945-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4b945-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b945-107">See Also</span></span>  
 [<span data-ttu-id="4b945-108">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="4b945-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="4b945-109">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="4b945-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="4b945-110">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="4b945-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="4b945-111">Oznámení změn v datové vazbě Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b945-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
