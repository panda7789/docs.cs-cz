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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="d973a-102">Postupy: Přidání vlastního prostoru do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="d973a-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="d973a-103">Výchozí hodnota otevřít a uložit dialogových oken na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] mít oblast na levé straně dialogového okna s názvem **Oblíbené odkazy**.</span><span class="sxs-lookup"><span data-stu-id="d973a-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="d973a-104">Tato oblast se nazývá vlastní místa.</span><span class="sxs-lookup"><span data-stu-id="d973a-104">This area is called custom places.</span></span> <span data-ttu-id="d973a-105"><xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy umožňují přidání složek do <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="d973a-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d973a-106">V pořadí pro vlastní místo, kde můžete zobrazit v <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> musí být nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d973a-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="d973a-107">Chcete-li přidat vlastní místo do dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="d973a-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="d973a-108">Přidejte cestu známé složky GUID, nebo <xref:System.Windows.Forms.FileDialogCustomPlace> do objektu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> kolekce dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="d973a-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="d973a-109">Následující příklad kódu ukazuje, jak přidat cestu:</span><span class="sxs-lookup"><span data-stu-id="d973a-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d973a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d973a-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d973a-111">Známé identifikátory GUID pro vlastní místa dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="d973a-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
