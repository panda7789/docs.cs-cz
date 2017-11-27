---
title: "Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView"
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
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d9a8bdc54f3f321b37bda897aac1f340f7a46aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="6743c-102">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="6743c-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="6743c-103">Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek může zobrazit ikony ze tří seznamů obrázků.</span><span class="sxs-lookup"><span data-stu-id="6743c-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="6743c-104">Zobrazení seznamu, podrobnosti a SmallIcon zobrazení obrázků ze seznamu obrázků zadaný v <xref:System.Windows.Forms.ListView.SmallImageList%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6743c-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="6743c-105">Zobrazuje obrázků ze seznamu obrázků zadaný v zobrazení LargeIcon <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6743c-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="6743c-106">Zobrazení seznamu lze také zobrazit další sadu ikony, nastavte v <xref:System.Windows.Forms.ListView.StateImageList%2A> vlastnost vedle velké nebo malé ikony.</span><span class="sxs-lookup"><span data-stu-id="6743c-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="6743c-107">Další informace o seznamech obrázků najdete v tématu [ImageList – komponenta](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) a [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="6743c-107">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="6743c-108">Pro zobrazení obrázků v zobrazení seznamu</span><span class="sxs-lookup"><span data-stu-id="6743c-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="6743c-109">Nastavte vlastnost odpovídající –<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, nebo <xref:System.Windows.Forms.ListView.StateImageList%2A>– ke stávající <xref:System.Windows.Forms.ImageList> součásti, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6743c-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="6743c-110">Tyto vlastnosti můžete nastavit v návrháři se okno Vlastnosti, nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="6743c-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="6743c-111">Nastavte <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> nebo <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> vlastnosti pro každou položku seznamu, který má přidružené ikonu.</span><span class="sxs-lookup"><span data-stu-id="6743c-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="6743c-112">Tyto vlastnosti lze nastavit v kódu nebo uvnitř **Editor kolekce ListViewItem**.</span><span class="sxs-lookup"><span data-stu-id="6743c-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="6743c-113">Chcete-li otevřít **Editor kolekce ListViewItem**, klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle <xref:System.Windows.Forms.ListView.Items%2A>vlastnost **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="6743c-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="6743c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6743c-114">See Also</span></span>  
 [<span data-ttu-id="6743c-115">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="6743c-115">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="6743c-116">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6743c-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="6743c-117">Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6743c-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="6743c-118">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6743c-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="6743c-119">ImageList – komponenta</span><span class="sxs-lookup"><span data-stu-id="6743c-119">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
