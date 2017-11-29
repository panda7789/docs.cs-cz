---
title: "Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cadf31d45f8650336c6ac6257a84655a978a9035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="03c40-102">Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="03c40-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="03c40-103">Dlaždice zobrazení funkce <xref:System.Windows.Forms.ListView> řízení umožňuje zadat visual rovnováhu mezi grafické a textové informace.</span><span class="sxs-lookup"><span data-stu-id="03c40-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="03c40-104">Textové informace zobrazené položky v dlaždici zobrazení je stejný jako informace o sloupci definována pro zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="03c40-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="03c40-105">Označit funkcí v dlaždici zobrazit funkce v kombinaci s seskupení nebo vložení <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="03c40-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="03c40-106">Zobrazení tile používá ikonou 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="03c40-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="03c40-107">![Dlaždicové zobrazení v ovládacím prvku ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="03c40-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="03c40-108">Dlaždice zobrazení, vlastnosti a metody umožňují určit, která pole sloupce k zobrazení pro každou položku a souhrnně řídí velikost a vzhled všechny položky v rámci časového období zobrazení dlaždice.</span><span class="sxs-lookup"><span data-stu-id="03c40-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="03c40-109">Pro přehlednost první řádek textu v dlaždici je vždy název položky; nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="03c40-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="03c40-110">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="03c40-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="03c40-111">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="03c40-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03c40-112">Je k dispozici pouze v dlaždici zobrazení [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="03c40-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="03c40-113">V dřívějších operačních systémech, všechny kód týkající se zobrazení tile nemá žádný vliv a <xref:System.Windows.Forms.ListView> zobrazí v zobrazení velkých ikon.</span><span class="sxs-lookup"><span data-stu-id="03c40-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="03c40-114">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03c40-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="03c40-115">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="03c40-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="03c40-116">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="03c40-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="03c40-117">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="03c40-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="03c40-118">Chcete-li nastavit zobrazení tile v Návrháři</span><span class="sxs-lookup"><span data-stu-id="03c40-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="03c40-119">Vyberte <xref:System.Windows.Forms.ListView> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="03c40-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="03c40-120">V **vlastnosti** vyberte <xref:System.Windows.Forms.ListView.View%2A> vlastnost a zvolte **dlaždice**.</span><span class="sxs-lookup"><span data-stu-id="03c40-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c40-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="03c40-121">See Also</span></span>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="03c40-122">Funkce systému Windows XP a Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="03c40-122">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="03c40-123">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="03c40-123">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
