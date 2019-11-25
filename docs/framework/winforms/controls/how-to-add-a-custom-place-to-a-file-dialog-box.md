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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="03993-102">Postupy: Přidání vlastního prostoru do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="03993-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="03993-103">Výchozí dialogová okna otevřít a uložit v systému Windows Vista mají oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**.</span><span class="sxs-lookup"><span data-stu-id="03993-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="03993-104">Tato oblast se nazývá vlastní místa.</span><span class="sxs-lookup"><span data-stu-id="03993-104">This area is called custom places.</span></span> <span data-ttu-id="03993-105">Třídy <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> umožňují přidávat složky do kolekce <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.</span><span class="sxs-lookup"><span data-stu-id="03993-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03993-106">Aby se vlastní místo zobrazilo v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, musí být vlastnost <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="03993-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="03993-107">Přidání vlastního místa do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="03993-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="03993-108">Přidejte cestu, identifikátor GUID známé složky nebo objekt <xref:System.Windows.Forms.FileDialogCustomPlace> do kolekce <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="03993-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="03993-109">Následující příklad kódu ukazuje, jak přidat cestu:</span><span class="sxs-lookup"><span data-stu-id="03993-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="03993-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03993-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03993-111">Známé identifikátory GUID složek pro vlastní místa dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="03993-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
