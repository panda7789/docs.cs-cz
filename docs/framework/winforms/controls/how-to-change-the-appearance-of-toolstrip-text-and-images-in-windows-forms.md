---
title: 'Postupy: Změna vzhledu textu a obrázků ToolStrip'
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
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746605"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="15b37-102">Postupy: Změna vzhledu textu a obrázků ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15b37-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="15b37-103">Můžete určit, zda se text a obrázky zobrazí na <xref:System.Windows.Forms.ToolStripItem> a jak jsou zarovnány relativně k sobě navzájem a <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="15b37-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="15b37-104">Definování obsahu zobrazeného na ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="15b37-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="15b37-105">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15b37-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="15b37-106">Možnosti jsou `Image`, `ImageAndText`, `None`a `Text`.</span><span class="sxs-lookup"><span data-stu-id="15b37-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="15b37-107">Výchozí formát je `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="15b37-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="15b37-108">Zarovnání textu v prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="15b37-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="15b37-109">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15b37-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="15b37-110">Možnosti jsou jakékoli kombinace horní, prostřední a dolní části s levou, střední a pravou.</span><span class="sxs-lookup"><span data-stu-id="15b37-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="15b37-111">Výchozí formát je `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="15b37-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="15b37-112">Zarovnání obrázku v prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="15b37-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="15b37-113">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15b37-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="15b37-114">Možnosti jsou jakékoli kombinace horní, prostřední a dolní části s levou, střední a pravou.</span><span class="sxs-lookup"><span data-stu-id="15b37-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="15b37-115">Výchozí formát je `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="15b37-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="15b37-116">Definování způsobu vzájemného zobrazení textu a obrázků prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="15b37-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="15b37-117">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15b37-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="15b37-118">Tyto možnosti jsou `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`a `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="15b37-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="15b37-119">Výchozí formát je `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="15b37-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="15b37-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="15b37-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="15b37-121">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="15b37-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="15b37-122">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="15b37-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="15b37-123">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="15b37-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
