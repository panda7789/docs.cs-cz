---
title: 'Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149523"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="e64d6-102">Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky</span><span class="sxs-lookup"><span data-stu-id="e64d6-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="e64d6-103">Tento příklad ukazuje, jak vytvořit standardní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno s použitím <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="e64d6-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e64d6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e64d6-104">Example</span></span>  
 <span data-ttu-id="e64d6-105">Následující příklad vytvoří dialogové okno podobné **spustit** dialogovém [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e64d6-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="e64d6-106">V příkladu se vytvoří <xref:System.Windows.Controls.Grid> a používá <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> tříd k definování pět sloupců a čtyři řádky.</span><span class="sxs-lookup"><span data-stu-id="e64d6-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="e64d6-107">V příkladu se pak přidá a umístí <xref:System.Windows.Controls.Image>, `RunIcon.png`, představující obrázek, který se nachází v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="e64d6-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="e64d6-108">Na obrázku je umístěn v prvním sloupci a řádku <xref:System.Windows.Controls.Grid> (levý horní roh).</span><span class="sxs-lookup"><span data-stu-id="e64d6-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="e64d6-109">V dalším kroku příklad přidá <xref:System.Windows.Controls.TextBlock> element na první sloupec, který zahrnuje zbývající sloupce na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="e64d6-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="e64d6-110">Přidá další <xref:System.Windows.Controls.TextBlock> element na druhém řádku v prvním sloupci znázornit **otevřít** textového pole.</span><span class="sxs-lookup"><span data-stu-id="e64d6-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="e64d6-111">A <xref:System.Windows.Controls.TextBlock> způsobem, která představuje vstupní datové oblasti.</span><span class="sxs-lookup"><span data-stu-id="e64d6-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="e64d6-112">Nakonec příklad přidá tři <xref:System.Windows.Controls.Button> elementy na posledním řádku, které představují **OK**, **zrušit**, a **Procházet** události.</span><span class="sxs-lookup"><span data-stu-id="e64d6-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e64d6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e64d6-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="e64d6-114">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="e64d6-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="e64d6-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e64d6-115">How-to Topics</span></span>](grid-how-to-topics.md)
