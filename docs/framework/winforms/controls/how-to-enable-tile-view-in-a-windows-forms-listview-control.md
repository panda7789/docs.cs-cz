---
title: 'Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48227f25126fe1d68391db7cd59edac450939381
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="81eb0-102">Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="81eb0-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="81eb0-103">Dlaždice zobrazení funkce k <xref:System.Windows.Forms.ListView> řízení, můžete zadat visual rovnováhu mezi grafické a textové informace.</span><span class="sxs-lookup"><span data-stu-id="81eb0-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="81eb0-104">Textové informace zobrazené položky v dlaždici zobrazení je stejný jako informace o sloupci definována pro zobrazení podrobností.</span><span class="sxs-lookup"><span data-stu-id="81eb0-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="81eb0-105">Dlaždice zobrazení funguje v kombinaci s seskupení nebo vložení označit funkcí v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="81eb0-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="81eb0-106">Zobrazení tile používá ikonou 32 x 32 pixelů a několik řádků textu, jak je znázorněno v následující bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="81eb0-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="81eb0-107">![Dlaždicové zobrazení v ovládacím prvku ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="81eb0-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
<span data-ttu-id="81eb0-108">Dlaždice zobrazení ikon a text.</span><span class="sxs-lookup"><span data-stu-id="81eb0-108">Tile view icons and text</span></span>  
  
 <span data-ttu-id="81eb0-109">Chcete-li povolit zobrazení vedle sebe, nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="81eb0-109">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="81eb0-110">Můžete upravit velikost dlaždic nastavením <xref:System.Windows.Forms.ListView.TileSize%2A> vlastnost a počet řádků textu zobrazí na dlaždici úpravou <xref:System.Windows.Forms.ListView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="81eb0-110">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81eb0-111">Je k dispozici pouze v dlaždici zobrazení [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="81eb0-111">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="81eb0-112">V dřívějších operačních systémech, všechny kód týkající se zobrazení tile nemá žádný vliv a <xref:System.Windows.Forms.ListView> zobrazí v zobrazení velkých ikon.</span><span class="sxs-lookup"><span data-stu-id="81eb0-112">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="81eb0-113">Další informace naleznete v tématu <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81eb0-113">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="81eb0-114">Chcete-li nastavit zobrazení tile prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="81eb0-114">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="81eb0-115">Použití <xref:System.Windows.Forms.View> výčet <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="81eb0-115">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="81eb0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="81eb0-116">Example</span></span>  
 <span data-ttu-id="81eb0-117">Následující příklad kompletní kód ukazuje zobrazení Tile s dlaždice upravit tak, aby zobrazit tři řádky textu.</span><span class="sxs-lookup"><span data-stu-id="81eb0-117">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="81eb0-118">Aby se zabránilo zalomení řádků bylo změněno velikost dlaždice.</span><span class="sxs-lookup"><span data-stu-id="81eb0-118">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81eb0-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="81eb0-119">Compiling the Code</span></span>  
 <span data-ttu-id="81eb0-120">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="81eb0-120">This example requires:</span></span>  
  
-   <span data-ttu-id="81eb0-121">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="81eb0-121">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="81eb0-122">Soubor ikony s názvem book.ico ve stejném adresáři jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="81eb0-122">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="81eb0-123">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="81eb0-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="81eb0-124">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="81eb0-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="81eb0-125">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="81eb0-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81eb0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="81eb0-126">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="81eb0-127">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="81eb0-127">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="81eb0-128">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="81eb0-128">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="81eb0-129">Funkce systému Windows XP a Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="81eb0-129">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
