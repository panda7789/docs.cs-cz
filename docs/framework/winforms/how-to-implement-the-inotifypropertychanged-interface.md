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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Postupy: Implementace rozhraní INotifyPropertyChanged
Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Toto rozhraní implementujte na obchodní objekty, které se používají v systému Windows Forms – datová vazba. Po implementaci rozhraní komunikuje připojeného ovládacího prvku změny vlastnost u objektu firmy.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití vzoru PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Postupy: vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged rozhraní](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Oznámení změn v systému Windows Forms datové vazby](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
