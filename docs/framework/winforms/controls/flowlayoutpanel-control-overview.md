---
title: FlowLayoutPanel – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526722"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="73ce3-102">FlowLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="73ce3-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="73ce3-103"><xref:System.Windows.Forms.FlowLayoutPanel> Řízení uspořádá jeho obsah v směr toku vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="73ce3-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="73ce3-104">Může obtékat obsah ovládacího prvku z jeden řádek na další, nebo z jednoho sloupce na další.</span><span class="sxs-lookup"><span data-stu-id="73ce3-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="73ce3-105">Místo wrap můžete alternativně oříznutí její obsah.</span><span class="sxs-lookup"><span data-stu-id="73ce3-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="73ce3-106">Směr toku můžete zadat nastavení hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73ce3-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="73ce3-107"><xref:System.Windows.Forms.FlowLayoutPanel> Řízení správně obrátí jeho směr toku v rozložení doleva (RTL).</span><span class="sxs-lookup"><span data-stu-id="73ce3-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="73ce3-108">Můžete také určit, zda <xref:System.Windows.Forms.FlowLayoutPanel> obsah ovládacího prvku zalomen nebo oříznut podle nastavení hodnoty <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73ce3-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="73ce3-109"><xref:System.Windows.Forms.FlowLayoutPanel> Řídit automaticky velikosti k jejímu obsahu při nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="73ce3-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="73ce3-110">Poskytuje také **FlowBreak** vlastnosti tak, aby jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="73ce3-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="73ce3-111">Nastavení hodnoty vlastnosti FlowBreak `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> řízení zastavit rozložení ovládacích prvků v aktuální směr toku a wrap na další řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="73ce3-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="73ce3-112">Libovolný ovládací prvek Windows Forms může být podřízená <xref:System.Windows.Forms.FlowLayoutPanel> řízení, včetně ostatní instance <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="73ce3-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="73ce3-113">Díky této funkci můžete vytvořit sofistikované rozložení, které přizpůsobit do svého formuláře dimenzí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="73ce3-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="73ce3-114">Viz také [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="73ce3-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ce3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="73ce3-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="73ce3-116">Ovládací prvek FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73ce3-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
