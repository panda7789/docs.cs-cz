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
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923418"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="5a465-102">Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky</span><span class="sxs-lookup"><span data-stu-id="5a465-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="5a465-103">Tento příklad ukazuje, jak vytvořit standardní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno <xref:System.Windows.Controls.Grid> pomocí elementu.</span><span class="sxs-lookup"><span data-stu-id="5a465-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a465-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a465-104">Example</span></span>  
 <span data-ttu-id="5a465-105">Následující příklad vytvoří dialogové okno, jako je dialogové okno **Spustit** v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5a465-105">The following example creates a dialog box like the **Run** dialog box in the Windows operating system.</span></span>  
  
 <span data-ttu-id="5a465-106">V příkladu se vytvoří <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.ColumnDefinition> pomocí tříd a <xref:System.Windows.Controls.RowDefinition> definuje pět sloupců a čtyři řádky.</span><span class="sxs-lookup"><span data-stu-id="5a465-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="5a465-107">Příklad následně přidá a umístí <xref:System.Windows.Controls.Image>do, `RunIcon.png`, aby představoval obrázek, který se nachází v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="5a465-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="5a465-108">Obrázek se umístí do prvního sloupce a řádku <xref:System.Windows.Controls.Grid> (v levém horním rohu).</span><span class="sxs-lookup"><span data-stu-id="5a465-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="5a465-109">Dále tento příklad přidá <xref:System.Windows.Controls.TextBlock> prvek do prvního sloupce, který zahrnuje zbývající sloupce prvního řádku.</span><span class="sxs-lookup"><span data-stu-id="5a465-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="5a465-110">Přidá další <xref:System.Windows.Controls.TextBlock> prvek do druhého řádku v prvním sloupci, který představuje **otevřené** textové pole.</span><span class="sxs-lookup"><span data-stu-id="5a465-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="5a465-111"><xref:System.Windows.Controls.TextBlock> Následuje, který představuje oblast pro zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="5a465-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="5a465-112">Nakonec <xref:System.Windows.Controls.Button> příklad přidá tři prvky do finálního řádku, které reprezentují události **OK**, **Zrušit**a **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="5a465-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5a465-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a465-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="5a465-114">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="5a465-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="5a465-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="5a465-115">How-to Topics</span></span>](grid-how-to-topics.md)
