---
title: 'Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView'
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
ms.openlocfilehash: 34e7025ab29ec2e0d2035fa07f2a6d53c2b197c9
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261710"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="45db1-102">Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="45db1-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="45db1-103">S funkcí zobrazení dlaždice <xref:System.Windows.Forms.ListView> ovládacího prvku, můžete zadat vizuální rovnováhu mezi textové a grafické informace.</span><span class="sxs-lookup"><span data-stu-id="45db1-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="45db1-104">Textové informace zobrazené položky v zobrazení tile je stejný jako sloupec informace definované pro zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="45db1-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="45db1-105">Zobrazení Tile funguje v kombinaci s funkcemi označit seskupení nebo vložení ve <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="45db1-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="45db1-106">Zobrazení tile používá ikony 32 x 32 pixelů a několik řádků textu, jak je znázorněno na následujících obrázcích.</span><span class="sxs-lookup"><span data-stu-id="45db1-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="45db1-107">![Dlaždice zobrazení v ovládacím prvku ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="45db1-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
<span data-ttu-id="45db1-108">Dlaždice zobrazení ikon a textu</span><span class="sxs-lookup"><span data-stu-id="45db1-108">Tile view icons and text</span></span>  
  
 <span data-ttu-id="45db1-109">Chcete-li povolit zobrazení tile, nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="45db1-109">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="45db1-110">Můžete nastavit velikost dlaždic tak, že nastavíte <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnost a počet řádků textu se zobrazí na dlaždici úpravou <xref:System.Windows.Forms.ListView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="45db1-110">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45db1-111">Je k dispozici pouze v zobrazení tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] když vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="45db1-111">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="45db1-112">Ve starších operačních systémech, jakýkoli kód související s zobrazení tile nemá žádný účinek a <xref:System.Windows.Forms.ListView> ovládací prvek zobrazí v zobrazení LargeIcon.</span><span class="sxs-lookup"><span data-stu-id="45db1-112">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="45db1-113">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45db1-113">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="45db1-114">Chcete-li nastavit zobrazení tile prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="45db1-114">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="45db1-115">Použití <xref:System.Windows.Forms.View> výčet <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="45db1-115">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="45db1-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="45db1-116">Example</span></span>  
 <span data-ttu-id="45db1-117">Následující příklad kompletní kód ukazuje zobrazení Tile s dlaždicemi, které upravit tak, aby zobrazit tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="45db1-117">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="45db1-118">Aby se zabránilo zalomení řádku bylo změněno velikosti dlaždice.</span><span class="sxs-lookup"><span data-stu-id="45db1-118">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45db1-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="45db1-119">Compiling the Code</span></span>  
 <span data-ttu-id="45db1-120">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="45db1-120">This example requires:</span></span>  
  
-   <span data-ttu-id="45db1-121">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="45db1-121">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="45db1-122">Soubor ikony s názvem book.ico ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="45db1-122">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="45db1-123">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="45db1-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="45db1-124">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="45db1-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45db1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45db1-125">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="45db1-126">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="45db1-126">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="45db1-127">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="45db1-127">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
