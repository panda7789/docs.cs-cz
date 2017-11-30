---
title: "Postupy: Přidání vlastního prostoru do dialogového okna souboru"
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
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ce5efccfd2efda2f333b51868e375849f7c7752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Postupy: Přidání vlastního prostoru do dialogového okna souboru
Výchozí hodnota otevřít a uložit dialogových oken na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] mít oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**. Tato oblast se nazývá vlastní místa. <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy umožňují přidání složek do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce.  
  
> [!NOTE]
>  V pořadí pro vlastní místo, kde můžete zobrazit v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být nastavena na `true` (výchozí).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Chcete-li přidat vlastní místo do dialogového okna souboru  
  
-   Přidejte cestu známé složky GUID, nebo <xref:System.Windows.Forms.FileDialogCustomPlace> do objektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce dialogového okna.  
  
     Následující příklad kódu ukazuje, jak přidat cestu:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [Známé identifikátory GUID pro vlastní místa dialogového okna souboru](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
