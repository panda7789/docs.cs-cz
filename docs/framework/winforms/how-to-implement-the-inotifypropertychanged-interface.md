---
title: 'Postupy: Implementace rozhraní INotifyPropertyChanged'
description: Naučte se implementovat rozhraní INotifyPropertyChanged pro obchodní objekty, které se používají v model Windows Forms datové vazby.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619265"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="f1fa5-103">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="f1fa5-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="f1fa5-104">Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1fa5-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="f1fa5-105">Implementujte toto rozhraní pro obchodní objekty, které se používají v model Windows Forms datové vazby.</span><span class="sxs-lookup"><span data-stu-id="f1fa5-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="f1fa5-106">Při implementaci rozhraní komunikuje s vázaným ovládacím prvkem o změnách vlastností u obchodního objektu.</span><span class="sxs-lookup"><span data-stu-id="f1fa5-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1fa5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1fa5-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f1fa5-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1fa5-108">See also</span></span>

- [<span data-ttu-id="f1fa5-109">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="f1fa5-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="f1fa5-110">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="f1fa5-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="f1fa5-111">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="f1fa5-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="f1fa5-112">Oznámení změn v datové vazbě rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1fa5-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
