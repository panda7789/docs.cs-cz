---
title: "Přehled ovládacího prvku Panel (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a><span data-ttu-id="bc608-102">Přehled ovládacího prvku Panel (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bc608-102">Panel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="bc608-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky používané k zajištění osobní seskupení pro další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bc608-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to provide an identifiable grouping for other controls.</span></span> <span data-ttu-id="bc608-104">Obvykle použijete panelů dále dělit formuláře podle funkce.</span><span class="sxs-lookup"><span data-stu-id="bc608-104">Typically, you use panels to subdivide a form by function.</span></span> <span data-ttu-id="bc608-105">Například můžete mít formulář objednávky, který určuje poštovní možnosti, například které přes noc poskytovatel používat.</span><span class="sxs-lookup"><span data-stu-id="bc608-105">For example, you may have an order form that specifies mailing options such as which overnight carrier to use.</span></span> <span data-ttu-id="bc608-106">Všechny možnosti panelu seskupení umožňuje uživateli logické vizuální upozornění.</span><span class="sxs-lookup"><span data-stu-id="bc608-106">Grouping all options in a panel gives the user a logical visual cue.</span></span> <span data-ttu-id="bc608-107">V návrhu čas všechny ovládací prvky lze snadno přesunout – když přesunete <xref:System.Windows.Forms.Panel> řídit, všechny její obsažené ovládací prvky příliš přesunout.</span><span class="sxs-lookup"><span data-stu-id="bc608-107">At design time all the controls can be moved easily — when you move the <xref:System.Windows.Forms.Panel> control, all its contained controls move, too.</span></span> <span data-ttu-id="bc608-108">Ovládací prvky jsou seskupené v panelu je přístupná přes jeho <xref:System.Windows.Forms.Control.Controls%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc608-108">The controls grouped in a panel can be accessed through its <xref:System.Windows.Forms.Control.Controls%2A> property.</span></span> <span data-ttu-id="bc608-109">Tato vlastnost vrátí kolekci <xref:System.Windows.Forms.Control> instance, takže obvykle bude potřeba převést ovládacího prvku načíst tento způsob, jak jeho konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="bc608-109">This property returns a collection of <xref:System.Windows.Forms.Control> instances, so you will typically need to cast a control retrieved this way to its specific type.</span></span>  
  
## <a name="panel-versus-groupbox"></a><span data-ttu-id="bc608-110">Panel Versus GroupBox</span><span class="sxs-lookup"><span data-stu-id="bc608-110">Panel Versus GroupBox</span></span>  
 <span data-ttu-id="bc608-111"><xref:System.Windows.Forms.Panel> Ovládací prvek je podobný <xref:System.Windows.Forms.GroupBox> řízení; však pouze <xref:System.Windows.Forms.Panel> ovládací prvek může mít posuvníky a jenom <xref:System.Windows.Forms.GroupBox> zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="bc608-111">The <xref:System.Windows.Forms.Panel> control is similar to the <xref:System.Windows.Forms.GroupBox> control; however, only the <xref:System.Windows.Forms.Panel> control can have scroll bars, and only the <xref:System.Windows.Forms.GroupBox> control displays a caption.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="bc608-112">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bc608-112">Key Properties</span></span>  
 <span data-ttu-id="bc608-113">Chcete-li zobrazit posuvníky, nastavte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="bc608-113">To display scroll bars, set the <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> property to `true`.</span></span> <span data-ttu-id="bc608-114">Můžete také přizpůsobit vzhled panelu nastavení <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, a <xref:System.Windows.Forms.Panel.BorderStyle%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bc608-114">You can also customize the appearance of the panel by setting the <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, and <xref:System.Windows.Forms.Panel.BorderStyle%2A> properties.</span></span> <span data-ttu-id="bc608-115">Další informace o <xref:System.Windows.Forms.Control.BackColor%2A> a <xref:System.Windows.Forms.Control.BackgroundImage%2A> najdete v části vlastnosti, [postupy: nastavení pozadí panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span><span class="sxs-lookup"><span data-stu-id="bc608-115">For more information on the <xref:System.Windows.Forms.Control.BackColor%2A> and <xref:System.Windows.Forms.Control.BackgroundImage%2A> properties, see [How to: Set the Background of a Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span></span> <span data-ttu-id="bc608-116"><xref:System.Windows.Forms.Panel.BorderStyle%2A> Vlastnost určuje, pokud je panel uvedených bez viditelné okraje (<xref:System.Windows.Forms.BorderStyle.None>), prostý řádku (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), nebo stíněné řádku (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span><span class="sxs-lookup"><span data-stu-id="bc608-116">The <xref:System.Windows.Forms.Panel.BorderStyle%2A> property determines if the panel is outlined with no visible border (<xref:System.Windows.Forms.BorderStyle.None>), a plain line (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), or a shadowed line (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc608-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc608-117">See Also</span></span>  
 <xref:System.Windows.Forms.Panel>  
 [<span data-ttu-id="bc608-118">Ovládací prvek GroupBox</span><span class="sxs-lookup"><span data-stu-id="bc608-118">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [<span data-ttu-id="bc608-119">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="bc608-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [<span data-ttu-id="bc608-120">Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="bc608-120">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
