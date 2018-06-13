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
ms.openlocfilehash: 7a6ace385f7594a467785fbc677517c8a6e1ab53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525736"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="a61f8-102">Postupy: Přidání vlastního prostoru do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="a61f8-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="a61f8-103">Výchozí hodnota otevřít a uložit dialogových oken na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] mít oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**.</span><span class="sxs-lookup"><span data-stu-id="a61f8-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="a61f8-104">Tato oblast se nazývá vlastní místa.</span><span class="sxs-lookup"><span data-stu-id="a61f8-104">This area is called custom places.</span></span> <span data-ttu-id="a61f8-105"><xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy umožňují přidání složek do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a61f8-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a61f8-106">V pořadí pro vlastní místo, kde můžete zobrazit v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a61f8-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="a61f8-107">Chcete-li přidat vlastní místo do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="a61f8-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="a61f8-108">Přidejte cestu známé složky GUID, nebo <xref:System.Windows.Forms.FileDialogCustomPlace> do objektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="a61f8-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="a61f8-109">Následující příklad kódu ukazuje, jak přidat cestu:</span><span class="sxs-lookup"><span data-stu-id="a61f8-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a61f8-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a61f8-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a61f8-111">Známé identifikátory GUID složek pro vlastní místa dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="a61f8-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
