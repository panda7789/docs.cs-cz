---
title: Přizpůsobení vzhledu řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744037"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6bb88-102">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6bb88-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6bb88-103">Můžete ovládat vzhled <xref:System.Windows.Forms.DataGridView> řádků tím, že zpracujete jednu nebo obě události <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bb88-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="6bb88-104">Tyto události jsou navržené tak, aby bylo možné malovat pouze ty, které chcete, a současně umožnit ovládacímu prvku <xref:System.Windows.Forms.DataGridView> malovat zbytek.</span><span class="sxs-lookup"><span data-stu-id="6bb88-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="6bb88-105">Například pokud chcete malovat vlastní pozadí, můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a nechat jednotlivé buňky malovat vlastní obsah v popředí.</span><span class="sxs-lookup"><span data-stu-id="6bb88-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="6bb88-106">Alternativně můžete nechat buňky malovat sami a přidat vlastní obsah v popředí obslužné rutiny pro událost <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bb88-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="6bb88-107">V obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> můžete také zakázat Malování buněk a malovat všechno sami.</span><span class="sxs-lookup"><span data-stu-id="6bb88-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="6bb88-108">Následující příklad kódu implementuje obslužné rutiny pro obě události, aby bylo možné poskytnout pozadí výběru barevného přechodu a určitý vlastní obsah v popředí, který pokrývá více sloupců.</span><span class="sxs-lookup"><span data-stu-id="6bb88-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb88-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bb88-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6bb88-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6bb88-110">Compiling the Code</span></span>  
 <span data-ttu-id="6bb88-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6bb88-111">This example requires:</span></span>  
  
- <span data-ttu-id="6bb88-112">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="6bb88-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb88-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bb88-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="6bb88-114">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6bb88-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6bb88-115">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="6bb88-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
