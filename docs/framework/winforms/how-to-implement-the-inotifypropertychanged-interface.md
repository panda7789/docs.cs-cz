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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Postupy: Implementace rozhraní INotifyPropertyChanged
Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Implementujte toto rozhraní pro obchodní objekty, které se používají v model Windows Forms datové vazby. Při implementaci rozhraní komunikuje s vázaným ovládacím prvkem o změnách vlastností u obchodního objektu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití vzoru PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Oznámení změn v datové vazbě rozhraní Windows Forms](change-notification-in-windows-forms-data-binding.md)
