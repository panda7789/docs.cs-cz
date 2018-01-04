---
title: "Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms"
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
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe88ff8d31a83b8516b11cd9aadd4bc2d4bf99a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="4bb88-102">Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4bb88-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="4bb88-103">Můžete řídit, jestli na zobrazení textu a obrázků <xref:System.Windows.Forms.ToolStripItem> a jakým způsobem je zarovnán relativně k sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="4bb88-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="4bb88-104">Chcete-li definovat, co se zobrazí na ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4bb88-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="4bb88-105">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4bb88-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="4bb88-106">Možnosti jsou `Image`, `ImageAndText`, `None`, a `Text`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="4bb88-107">Výchozí hodnota je `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="4bb88-108">Chcete-li zarovnat text na ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4bb88-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="4bb88-109">Nastavte <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4bb88-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="4bb88-110">Možnosti jsou libovolnou kombinaci nejvyšší, střední a dolní s vlevo, na střed a doprava.</span><span class="sxs-lookup"><span data-stu-id="4bb88-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="4bb88-111">Výchozí hodnota je `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="4bb88-112">Chcete-li zarovnat bitové kopie v prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4bb88-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="4bb88-113">Nastavte <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4bb88-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="4bb88-114">Možnosti jsou libovolnou kombinaci nejvyšší, střední a dolní s vlevo, na střed a doprava.</span><span class="sxs-lookup"><span data-stu-id="4bb88-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="4bb88-115">Výchozí hodnota je `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="4bb88-116">Chcete-li definovat zobrazení ToolStripItem textu a obrázků relativně k sobě navzájem</span><span class="sxs-lookup"><span data-stu-id="4bb88-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="4bb88-117">Nastavte <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4bb88-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="4bb88-118">Možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, a `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="4bb88-119">Výchozí hodnota je `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="4bb88-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4bb88-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bb88-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="4bb88-121">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4bb88-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="4bb88-122">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4bb88-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="4bb88-123">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4bb88-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
