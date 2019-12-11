---
title: 'Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 4f51d3a596bc3358942cdfd654b3e4515d96cd07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960095"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="9930f-102">Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9930f-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="9930f-103">Funkce zobrazení dlaždice ovládacího prvku <xref:System.Windows.Forms.ListView> umožňuje zadat vizuální vyvážení mezi grafickými a textovými informacemi.</span><span class="sxs-lookup"><span data-stu-id="9930f-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="9930f-104">Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="9930f-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="9930f-105">Funkce zobrazení dlaždic v kombinaci s funkcemi seskupení nebo vložení v ovládacím prvku <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="9930f-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="9930f-106">V zobrazení dlaždice se používá ikona 32 x 32 a několik řádků textu, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9930f-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="9930f-107">![Zobrazení dlaždic v ovládacím prvku ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Ikony a text dlaždicového zobrazení")</span><span class="sxs-lookup"><span data-stu-id="9930f-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="9930f-108">Vlastnosti a metody zobrazení dlaždic umožňují určit, která sloupcová pole se mají zobrazit pro každou položku, a pro souhrnnou kontrolu velikosti a vzhledu všech položek v okně zobrazení dlaždic.</span><span class="sxs-lookup"><span data-stu-id="9930f-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="9930f-109">Pro přehlednost je první řádek textu v dlaždici vždycky název položky; nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="9930f-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="9930f-110">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="9930f-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="9930f-111">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9930f-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="9930f-112">Nastavení zobrazení dlaždic v Návrháři</span><span class="sxs-lookup"><span data-stu-id="9930f-112">To set tile view in the designer</span></span>

1. <span data-ttu-id="9930f-113">V aplikaci Visual Studio vyberte ovládací prvek <xref:System.Windows.Forms.ListView> na formuláři.</span><span class="sxs-lookup"><span data-stu-id="9930f-113">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="9930f-114">V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.ListView.View%2A> a zvolte možnost **dlaždice**.</span><span class="sxs-lookup"><span data-stu-id="9930f-114">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9930f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9930f-115">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="9930f-116">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="9930f-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
