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
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976994"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Postupy: Přidání vlastního prostoru do dialogového okna souboru
Výchozí dialogová okna otevřít a uložit v systému Windows Vista mají oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**. Tato oblast se nazývá vlastní místa. Třídy <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> umožňují přidávat složky do kolekce <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.  
  
> [!NOTE]
> Aby se vlastní místo zobrazilo v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, musí být vlastnost <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> nastavena na `true` (výchozí).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Přidání vlastního místa do dialogového okna souboru  
  
- Přidejte cestu, identifikátor GUID známé složky nebo objekt <xref:System.Windows.Forms.FileDialogCustomPlace> do kolekce <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> dialogového okna.  
  
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
