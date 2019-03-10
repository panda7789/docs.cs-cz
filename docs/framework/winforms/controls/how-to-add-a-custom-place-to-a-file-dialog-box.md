---
title: 'Postupy: Přidání vlastního prostoru do dialogového okna souboru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: d9c1373a16f7d62c2933e01e513478fc6c9866d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721876"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Postupy: Přidání vlastního prostoru do dialogového okna souboru
Výchozí hodnota otevřít a uložit dialogových oknech na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] mají oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**. Tato oblast se nazývá vlastní místa. <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy umožňují přidat složky, které mají <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce.  
  
> [!NOTE]
>  Aby se vlastní místo, kde se zobrazí v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být vlastnost nastavena na `true` (výchozí).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>K přidání vlastního prostoru do dialogového okna souboru  
  
-   Přidejte cestu známé složky identifikátor GUID, nebo <xref:System.Windows.Forms.FileDialogCustomPlace> objektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce dialogového okna.  
  
     Následující příklad kódu ukazuje, jak přidat cestu:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [Známé identifikátory GUID složek pro vlastní místa dialogového okna souboru](known-folder-guids-for-file-dialog-custom-places.md)
