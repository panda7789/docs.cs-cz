---
title: Zobrazení obrázků v buňkách ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740287"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="93bea-102">Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="93bea-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="93bea-103">Obrázek nebo obrázek je jednou z hodnot, které lze zobrazit v řádku dat.</span><span class="sxs-lookup"><span data-stu-id="93bea-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="93bea-104">Tyto grafiky mají často formu fotografie zaměstnance nebo loga společnosti.</span><span class="sxs-lookup"><span data-stu-id="93bea-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="93bea-105">Zahrnutí obrázků je jednoduché při zobrazení dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="93bea-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="93bea-106">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nativně zpracovává libovolný formát obrázku podporovaný <xref:System.Drawing.Image> třídou a také formát obrázku OLE používaný některými databázemi.</span><span class="sxs-lookup"><span data-stu-id="93bea-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="93bea-107">Pokud zdroj dat ovládacího prvku <xref:System.Windows.Forms.DataGridView> obsahuje sloupec obrázků, bude automaticky zobrazen pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="93bea-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="93bea-108">Následující příklad kódu ukazuje, jak extrahovat ikonu z vloženého zdroje a převést ji na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku.</span><span class="sxs-lookup"><span data-stu-id="93bea-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="93bea-109">Další příklad, který nahradí hodnoty textové buňky odpovídajícími obrázky, naleznete v tématu [How to: Customizing Data Formatting in model Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="93bea-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93bea-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="93bea-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93bea-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="93bea-111">Compiling the Code</span></span>  
 <span data-ttu-id="93bea-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="93bea-112">This example requires:</span></span>  
  
- <span data-ttu-id="93bea-113"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="93bea-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="93bea-114">Vložený prostředek ikony s názvem `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="93bea-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="93bea-115">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>a <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93bea-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bea-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93bea-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="93bea-117">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="93bea-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="93bea-118">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="93bea-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
