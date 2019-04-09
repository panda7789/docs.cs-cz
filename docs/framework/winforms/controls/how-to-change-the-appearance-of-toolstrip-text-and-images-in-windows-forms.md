---
title: 'Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 5c326c8f6a56c934d317305f85f4c88e95e75f8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088468"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="bc1d9-102">Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc1d9-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="bc1d9-103">Můžete řídit, zda text a obrázky jsou zobrazeny na <xref:System.Windows.Forms.ToolStripItem> a jak jsou zarovnány relativně vůči sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="bc1d9-104">Chcete-li definovat, co se zobrazí na prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="bc1d9-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="bc1d9-105">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="bc1d9-106">Možnosti jsou `Image`, `ImageAndText`, `None`, a `Text`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="bc1d9-107">Výchozí hodnota je `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="bc1d9-108">Zarovnání textu v prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="bc1d9-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="bc1d9-109">Nastavte <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="bc1d9-110">Možnosti jsou kombinací nejvyšší, střední a dolní část s vlevo, na střed a doprava.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="bc1d9-111">Výchozí hodnota je `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="bc1d9-112">Chcete-li Zarovnat obrázek na prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="bc1d9-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="bc1d9-113">Nastavte <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="bc1d9-114">Možnosti jsou kombinací nejvyšší, střední a dolní část s vlevo, na střed a doprava.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="bc1d9-115">Výchozí hodnota je `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="bc1d9-116">Chcete-li definovat, jak ovládací prvek ToolStripItem text a obrázky se zobrazí relativně vůči sobě navzájem</span><span class="sxs-lookup"><span data-stu-id="bc1d9-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="bc1d9-117">Nastavte <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> vlastnost na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="bc1d9-118">Možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, a `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="bc1d9-119">Výchozí hodnota je `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="bc1d9-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc1d9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc1d9-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="bc1d9-121">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bc1d9-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="bc1d9-122">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bc1d9-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="bc1d9-123">Souhrn technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bc1d9-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
