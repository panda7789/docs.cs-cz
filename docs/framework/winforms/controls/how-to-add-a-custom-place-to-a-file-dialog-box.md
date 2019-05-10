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
ms.openlocfilehash: 129ebed6d0a2b075020e635c8463536f97629d2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624110"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8150c-102">Postupy: Přidání vlastního místa do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="8150c-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="8150c-103">Výchozí hodnota otevřít a uložit dialogových oknech na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] mají oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**.</span><span class="sxs-lookup"><span data-stu-id="8150c-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="8150c-104">Tato oblast se nazývá vlastní místa.</span><span class="sxs-lookup"><span data-stu-id="8150c-104">This area is called custom places.</span></span> <span data-ttu-id="8150c-105"><xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy umožňují přidat složky, které mají <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="8150c-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8150c-106">Aby se vlastní místo, kde se zobrazí v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být vlastnost nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8150c-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8150c-107">K přidání vlastního prostoru do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="8150c-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="8150c-108">Přidejte cestu známé složky identifikátor GUID, nebo <xref:System.Windows.Forms.FileDialogCustomPlace> objektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="8150c-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="8150c-109">Následující příklad kódu ukazuje, jak přidat cestu:</span><span class="sxs-lookup"><span data-stu-id="8150c-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8150c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8150c-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8150c-111">Známé identifikátory GUID složek pro vlastní místa dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="8150c-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
