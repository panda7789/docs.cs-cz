---
title: "TableLayoutPanel – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f8f949edcf637f4b56ab0bcfdd121c5cb29e543
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="1a79d-102">TableLayoutPanel – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1a79d-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="1a79d-103"><xref:System.Windows.Forms.TableLayoutPanel> Řízení uspořádá jeho obsah v mřížce.</span><span class="sxs-lookup"><span data-stu-id="1a79d-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="1a79d-104">Protože je prováděna rozložení i v době návrhu a běh, ho můžete změnit dynamicky jako změny prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="1a79d-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="1a79d-105">To umožňuje ovládacích prvků v panelu se úměrně změnit velikost, tak může reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka změna z důvodu lokalizace.</span><span class="sxs-lookup"><span data-stu-id="1a79d-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a79d-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1a79d-106">In This Section</span></span>  
 [<span data-ttu-id="1a79d-107">Přehled ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a79d-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="1a79d-108">Představuje obecné koncepty <xref:System.Windows.Forms.TableLayoutPanel> řízení, které vám umožní vytvořit rozložení řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="1a79d-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="1a79d-109">Osvědčené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a79d-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="1a79d-110">Popisuje doporučení, které vám pomohou naplno rozložení funkce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1a79d-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="1a79d-111">Chování AutoSize v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a79d-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="1a79d-112">Popisuje způsoby, ve kterém <xref:System.Windows.Forms.TableLayoutPanel> řízení podporuje chování Automatická změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="1a79d-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="1a79d-113">Postupy: ukotvení a dokování podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a79d-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="1a79d-114">Ukazuje, jak ukotvení a dokování podřízených ovládacích prvků v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1a79d-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="1a79d-115">Postupy: Návrh rozložení, který odpovídá lokalizaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a79d-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="1a79d-116">Ukazuje, jak pomocí <xref:System.Windows.Forms.TableLayoutPanel> řízení vytvořit formulář, který odpovídá lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="1a79d-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="1a79d-117">Postupy: vytvoření formuláře Windows s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="1a79d-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="1a79d-118">Ukazuje, jak pomocí <xref:System.Windows.Forms.TableLayoutPanel> řízení vytvořit formulář, který odpovídá Změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="1a79d-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  <span data-ttu-id="1a79d-119">[Postupy: zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a79d-119">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="1a79d-120">[Postupy: rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a79d-120">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="1a79d-121">[Postupy: upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a79d-121">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="1a79d-122">[Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a79d-122">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a79d-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1a79d-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="1a79d-124">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1a79d-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="1a79d-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.TableLayoutSettings> typu.</span><span class="sxs-lookup"><span data-stu-id="1a79d-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="1a79d-126">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1a79d-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a79d-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1a79d-127">Related Sections</span></span>  
 [<span data-ttu-id="1a79d-128">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="1a79d-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="1a79d-129">Poskytuje přehled témata týkající se lokalizace.</span><span class="sxs-lookup"><span data-stu-id="1a79d-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="1a79d-130">Viz také [lokalizace aplikací](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) nebo [lokalizace aplikací](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="1a79d-130">Also see [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) or [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span></span>
