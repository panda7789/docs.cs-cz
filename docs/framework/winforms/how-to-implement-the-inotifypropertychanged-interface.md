---
title: 'Postupy: Implementace rozhraní INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225596"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Postupy: Implementace rozhraní INotifyPropertyChanged
Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Toto rozhraní implementují pro obchodní objekty, které se používají ve Windows Forms – datová vazba. Po implementaci rozhraní komunikuje vázaného ovládacího prvku změny vlastností na obchodní objekt.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití vzoru PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Postupy: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní](./controls/raise-change-notifications--bindingsource.md)
- [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)
