---
title: 'Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013397"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="23967-102">Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="23967-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="23967-103">Obrázek nebo obrázek je jedna z hodnot zobrazených dat za sebou.</span><span class="sxs-lookup"><span data-stu-id="23967-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="23967-104">Často tyto grafiky podobu zaměstnance fotografie nebo logo společnosti.</span><span class="sxs-lookup"><span data-stu-id="23967-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="23967-105">Zahrnutí obrázky je jednoduché, pokud zobrazení dat v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="23967-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="23967-106"><xref:System.Windows.Forms.DataGridView> Nativně zpracovává všechny formát obrázku, který podporuje ovládací prvek <xref:System.Drawing.Image> třídy, jakož i OLE obrázek formát používaný některé databáze.</span><span class="sxs-lookup"><span data-stu-id="23967-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="23967-107">Pokud <xref:System.Windows.Forms.DataGridView> zdroj dat ovládacího prvku má sloupec bitových kopií, budou automaticky zobrazeny <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="23967-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="23967-108">Následující příklad kódu ukazuje, jak extrahovat ikonu ze vloženého prostředku a převod na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku.</span><span class="sxs-lookup"><span data-stu-id="23967-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="23967-109">Další příklad, který nahradí hodnoty textovou buňky odpovídající Image, najdete v části [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="23967-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23967-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="23967-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23967-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="23967-111">Compiling the Code</span></span>  
 <span data-ttu-id="23967-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="23967-112">This example requires:</span></span>  
  
- <span data-ttu-id="23967-113">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="23967-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="23967-114">Na ikonu vloženého prostředek s názvem `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="23967-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="23967-115">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="23967-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23967-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23967-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="23967-117">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="23967-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="23967-118">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="23967-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
