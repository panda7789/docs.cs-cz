---
title: 'Postupy: Přidání vlastního místa do dialogového okna souboru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916340"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Postupy: Přidání vlastního místa do dialogového okna souboru
Výchozí dialogová okna otevřít a uložit v [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] oblasti mají oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**. Tato oblast se nazývá vlastní místa. Třídy <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> a <xref:System.Windows.Forms.SaveFileDialog> umožňují přidat složky do kolekce.  
  
> [!NOTE]
> Aby se vlastní <xref:System.Windows.Forms.OpenFileDialog> místo zobrazovalo v nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být vlastnost nastavena na `true` (výchozí).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Přidání vlastního místa do dialogového okna souboru  
  
- Přidejte cestu, identifikátor GUID známé složky nebo <xref:System.Windows.Forms.FileDialogCustomPlace> objekt <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> do kolekce dialogového okna.  
  
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
