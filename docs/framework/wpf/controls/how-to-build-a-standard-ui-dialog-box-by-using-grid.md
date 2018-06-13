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
ms.openlocfilehash: d0b24e320c2a341b069e1c9c3e8b6d5e93076733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551879"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="baee0-102">Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky</span><span class="sxs-lookup"><span data-stu-id="baee0-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="baee0-103">Tento příklad ukazuje, jak vytvořit standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno pomocí <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="baee0-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baee0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="baee0-104">Example</span></span>  
 <span data-ttu-id="baee0-105">Následující příklad vytvoří dialogové okno podobné **spustit** dialogovém okně [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému.</span><span class="sxs-lookup"><span data-stu-id="baee0-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="baee0-106">V příkladu se vytváří <xref:System.Windows.Controls.Grid> a používá <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> třídy k definování pět sloupců a řádků čtyři.</span><span class="sxs-lookup"><span data-stu-id="baee0-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="baee0-107">V příkladu se pak přidá a umisťuje <xref:System.Windows.Controls.Image>, `RunIcon.png`, účelem zastoupení obrázku, která se nachází v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="baee0-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="baee0-108">Obrázek je umístěn v první sloupec a řádek <xref:System.Windows.Controls.Grid> (levého horního rohu).</span><span class="sxs-lookup"><span data-stu-id="baee0-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="baee0-109">V dalším kroku v příkladu přidáme <xref:System.Windows.Controls.TextBlock> element první sloupec, který zahrnuje zbývající sloupce prvního řádku.</span><span class="sxs-lookup"><span data-stu-id="baee0-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="baee0-110">Přidá další <xref:System.Windows.Controls.TextBlock> element na druhý řádek v první sloupec, aby reprezentoval **otevřete** textové pole.</span><span class="sxs-lookup"><span data-stu-id="baee0-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="baee0-111">A <xref:System.Windows.Controls.TextBlock> způsobem, která představuje vstupní data oblast.</span><span class="sxs-lookup"><span data-stu-id="baee0-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="baee0-112">Nakonec v příkladu přidáme tři <xref:System.Windows.Controls.Button> elementy poslední řádek, které představují **OK**, **zrušit**, a **Procházet** události.</span><span class="sxs-lookup"><span data-stu-id="baee0-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="baee0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="baee0-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [<span data-ttu-id="baee0-114">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="baee0-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="baee0-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="baee0-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
