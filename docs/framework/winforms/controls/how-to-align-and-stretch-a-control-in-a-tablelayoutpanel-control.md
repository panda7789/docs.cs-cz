---
title: 'Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210368"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="bdcb3-102">Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bdcb3-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>

<span data-ttu-id="bdcb3-103">Můžete zarovnání a roztažení ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> s <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>

## <a name="align-and-stretch-a-control"></a><span data-ttu-id="bdcb3-104">Zarovnání a roztažení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="bdcb3-104">Align and stretch a control</span></span>

1. <span data-ttu-id="bdcb3-105">V sadě Visual Studio, přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-105">In Visual Studio, drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="bdcb3-106">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="bdcb3-107"><xref:System.Windows.Forms.Button> Ovládací prvek je uprostřed buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-107">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>

3. <span data-ttu-id="bdcb3-108">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-108">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="bdcb3-109"><xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly šířka buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-109">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>

4. <span data-ttu-id="bdcb3-110">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-110">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="bdcb3-111"><xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly výška buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-111">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>

5. <span data-ttu-id="bdcb3-112">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-112">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="bdcb3-113"><xref:System.Windows.Forms.Button> Ovládací prvek roztáhne a vyplní buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-113">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>

6. <span data-ttu-id="bdcb3-114">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-114">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="bdcb3-115"><xref:System.Windows.Forms.Button> Ovládací prvek vrátí na původní velikost a přesune do levého horního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-115">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="bdcb3-116">**Návrháře formulářů Windows** nastavil <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-116">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>

7. <span data-ttu-id="bdcb3-117">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="bdcb3-118"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune do pravého dolního rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-118">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>

8. <span data-ttu-id="bdcb3-119">Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-119">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="bdcb3-120"><xref:System.Windows.Forms.Button> Ovládacího prvku přesune na střed buňku.</span><span class="sxs-lookup"><span data-stu-id="bdcb3-120">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdcb3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdcb3-121">See also</span></span>

- [<span data-ttu-id="bdcb3-122">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bdcb3-122">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
