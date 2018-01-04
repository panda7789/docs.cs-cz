---
title: "Postupy: Použití vzoru PropertyNameChanged"
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
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe397a92ac6e79e84757baa0c41f6e0c54b7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Postupy: Použití vzoru PropertyNameChanged
Následující příklad kódu ukazuje, jak se má použít *PropertyName*změněno vzor vlastního ovládacího prvku. Použít tento vzor při implementaci vlastní ovládací prvky, které se používají s modulem vazby dat Windows Forms.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace předchozí příklad kódu:  
  
-   Vložte kód do souboru prázdný kód. Je nutné použít vlastní ovládací prvek na formuláři, který obsahuje `Main` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Implementace rozhraní INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
