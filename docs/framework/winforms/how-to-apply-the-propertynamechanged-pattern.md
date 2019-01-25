---
title: 'Postupy: Použití vzoru PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 82856405ab3c9581b398f358e5bf9ecf989ce193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539763"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Postupy: Použití vzoru PropertyNameChanged
Následující příklad kódu ukazuje, jak použít *PropertyName*změněné vzor, který má vlastní ovládací prvek. Tento model použijte při implementaci vlastní ovládací prvky, které se používají s modulem Windows Forms datové vazby.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat v předchozím příkladu kódu:  
  
-   Vložte kód do prázdný soubor kódu. Je nutné použít vlastní ovládací prvek na formuláři Windows, který obsahuje `Main` metoda.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Implementace rozhraní INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
