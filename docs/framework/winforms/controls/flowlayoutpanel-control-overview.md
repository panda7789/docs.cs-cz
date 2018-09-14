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
ms.openlocfilehash: 73767114da1c04222fb8ceaf812153421c4597aa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517759"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="37541-102">FlowLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="37541-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="37541-103"><xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek uspořádá jeho obsah ve směru toku vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="37541-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="37541-104">Můžete zabalit obsah ovládacího prvku z jednoho řádku na další nebo z jednoho sloupce na další.</span><span class="sxs-lookup"><span data-stu-id="37541-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="37541-105">Namísto obtékání můžete alternativně oříznout jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="37541-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="37541-106">Směr toku můžete zadat tak, že nastavíte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37541-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="37541-107"><xref:System.Windows.Forms.FlowLayoutPanel> Ovládacího prvku správně obrátí jeho směr toku v rozložení doleva (RTL).</span><span class="sxs-lookup"><span data-stu-id="37541-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="37541-108">Můžete také určit, zda <xref:System.Windows.Forms.FlowLayoutPanel> obsah ovládacího prvku zalomen nebo oříznut tak, že nastavíte hodnotu <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37541-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="37541-109"><xref:System.Windows.Forms.FlowLayoutPanel> Automaticky řídit velikosti jeho obsah, při nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="37541-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="37541-110">Poskytuje také **FlowBreak** vlastnost jeho podřízeným ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="37541-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="37541-111">Nastavení hodnoty vlastnosti FlowBreak k `true` způsobí, že <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek zastavit rozvrhování ovládacích prvků v aktuální směr toku a zalomení na další řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="37541-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="37541-112">Libovolný ovládací prvek Windows Forms může být podřízený <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek, včetně dalších instancí <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="37541-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="37541-113">Díky této možnosti lze vytvořit sofistikované rozložení, které se přizpůsobí vaše formuláře dimenzí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="37541-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="37541-114">Viz také [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="37541-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37541-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="37541-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="37541-116">Ovládací prvek FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="37541-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
