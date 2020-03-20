---
title: Povolení zobrazení dlaždic v ovládacím prvku ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182156"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="3bdc0-102">Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="3bdc0-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="3bdc0-103">Pomocí funkce zobrazení dlaždic <xref:System.Windows.Forms.ListView> ovládacího prvku můžete zajistit vizuální rovnováhu mezi grafickými a textovými informacemi.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="3bdc0-104">Textové informace zobrazené pro položku v zobrazení dlaždic jsou stejné jako informace o sloupci definované pro zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="3bdc0-105">Zobrazení dlaždic funguje v kombinaci s prvky seskupení <xref:System.Windows.Forms.ListView> nebo značky vložení v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="3bdc0-106">Zobrazení dlaždic používá ikonu 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="3bdc0-107">![Zobrazení dlaždic v ovládacím prvku ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony a text zobrazení dlaždic")</span><span class="sxs-lookup"><span data-stu-id="3bdc0-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  

 <span data-ttu-id="3bdc0-108">Chcete-li povolit <xref:System.Windows.Forms.ListView.View%2A> zobrazení <xref:System.Windows.Forms.View.Tile>dlaždic, nastavte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="3bdc0-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="3bdc0-109">Velikost dlaždic můžete upravit nastavením <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnosti a počtu řádků textu zobrazených na dlaždici úpravou <xref:System.Windows.Forms.ListView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="3bdc0-110">Nastavení zobrazení dlaždic programově</span><span class="sxs-lookup"><span data-stu-id="3bdc0-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="3bdc0-111">Použijte <xref:System.Windows.Forms.View> výčet ovládacího <xref:System.Windows.Forms.ListView> prvku.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="3bdc0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bdc0-112">Example</span></span>  
 <span data-ttu-id="3bdc0-113">Následující příklad úplného kódu ukazuje zobrazení dlaždic s dlaždicemi upravenými tak, aby zobrazovaly tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="3bdc0-114">Velikost dlaždice byla upravena tak, aby se zabránilo zalamování řádků.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3bdc0-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3bdc0-115">Compiling the Code</span></span>  
 <span data-ttu-id="3bdc0-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3bdc0-116">This example requires:</span></span>  
  
- <span data-ttu-id="3bdc0-117">Odkazy na sestavení Systém u systému a systému.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="3bdc0-118">Soubor ikon s názvem book.ico ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3bdc0-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdc0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bdc0-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="3bdc0-120">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="3bdc0-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="3bdc0-121">ListView – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3bdc0-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
