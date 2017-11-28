---
title: "Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView"
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
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b2e06298d0ead9a2dd9fa554af0c42df5d61d56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="f08e4-102">Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f08e4-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f08e4-103">Obrázek nebo grafiku je jedna z hodnot, které můžete zobrazit v řádku dat.</span><span class="sxs-lookup"><span data-stu-id="f08e4-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="f08e4-104">Tato grafika často, mít formu zaměstnance fotografie nebo logo společnosti.</span><span class="sxs-lookup"><span data-stu-id="f08e4-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="f08e4-105">Zařadit obrázky je jednoduchá, při zobrazení dat v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f08e4-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f08e4-106"><xref:System.Windows.Forms.DataGridView> Nativně zpracovává všechny formát obrázku podporuje ovládací prvek <xref:System.Drawing.Image> třídy a také OLE obrázek formát používaný některé databáze.</span><span class="sxs-lookup"><span data-stu-id="f08e4-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="f08e4-107">Pokud <xref:System.Windows.Forms.DataGridView> ovládacího prvku zdroj dat má sloupec bitových kopií, zobrazí se automaticky pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f08e4-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="f08e4-108">Následující příklad kódu ukazuje, jak k extrahování ikony ze vloženého prostředku a ho převést na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku.</span><span class="sxs-lookup"><span data-stu-id="f08e4-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="f08e4-109">Další příklad, který nahrazuje hodnoty textovou buněk s odpovídající obrázky, naleznete v části [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f08e4-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f08e4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f08e4-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f08e4-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f08e4-111">Compiling the Code</span></span>  
 <span data-ttu-id="f08e4-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f08e4-112">This example requires:</span></span>  
  
-   <span data-ttu-id="f08e4-113">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f08e4-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="f08e4-114">Na ikonu vloženého prostředek s názvem `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="f08e4-114">An embedded icon resource named `tree.ico`.</span></span>  
  
-   <span data-ttu-id="f08e4-115">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="f08e4-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08e4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f08e4-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="f08e4-117">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f08e4-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="f08e4-118">Postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f08e4-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
