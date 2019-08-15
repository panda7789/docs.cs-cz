---
title: 'Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039690"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="8cd5e-102">Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8cd5e-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="8cd5e-103">Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvku mohou být rozloženy sousedícími řádky a sloupci.</span><span class="sxs-lookup"><span data-stu-id="8cd5e-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>

## <a name="to-span-columns-and-rows"></a><span data-ttu-id="8cd5e-104">Postup při rozpětí sloupců a řádků</span><span class="sxs-lookup"><span data-stu-id="8cd5e-104">To span columns and rows</span></span>

1. <span data-ttu-id="8cd5e-105">Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="8cd5e-105">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="8cd5e-106">Přetáhněte ovládací prvek ze **sady nástrojů** na <xref:System.Windows.Forms.TableLayoutPanel> levou horní buňku ovládacího prvku. <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="8cd5e-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="8cd5e-107">Nastavte vlastnost **jeho ColumnSpan**ovládacího prvku na hodnotu 2 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="8cd5e-107">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="8cd5e-108">Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek pokrývá první a druhý sloupec.</span><span class="sxs-lookup"><span data-stu-id="8cd5e-108">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>

4. <span data-ttu-id="8cd5e-109">Nastavte vlastnost **RowSpan**ovládacího prvku na hodnotu 2 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="8cd5e-109">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="8cd5e-110">Všimněte si, <xref:System.Windows.Forms.Button> že ovládací prvek pokrývá první a druhý řádek.</span><span class="sxs-lookup"><span data-stu-id="8cd5e-110">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>

5. <span data-ttu-id="8cd5e-111">Nastavte vlastnost **jeho ColumnSpan**ovládacího prvku na hodnotu 1 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="8cd5e-111">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="8cd5e-112">Všimněte si, <xref:System.Windows.Forms.Button> že se ovládací prvek přesune do prvního sloupce a zasahuje do prvního a druhého řádku.</span><span class="sxs-lookup"><span data-stu-id="8cd5e-112">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cd5e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cd5e-113">See also</span></span>

- [<span data-ttu-id="8cd5e-114">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8cd5e-114">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
