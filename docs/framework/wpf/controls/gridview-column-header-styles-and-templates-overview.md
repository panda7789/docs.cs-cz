---
title: "GridView Styly záhlaví sloupců a přehled šablon"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996d6d5f531a866d4fc80acc3848cdf264901032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="2539f-102">GridView Styly záhlaví sloupců a přehled šablon</span><span class="sxs-lookup"><span data-stu-id="2539f-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="2539f-103">Tento přehled popisuje pořadí priorit pro vlastnosti, které můžete použít k přizpůsobení v záhlaví sloupce <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2539f-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="2539f-104">Přizpůsobení záhlaví sloupce v GridView</span><span class="sxs-lookup"><span data-stu-id="2539f-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="2539f-105">Vlastnosti, které definují obsah, rozvržení a stylu záhlaví sloupce v <xref:System.Windows.Controls.GridView> jsou k dispozici v mnoha související třídy.</span><span class="sxs-lookup"><span data-stu-id="2539f-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="2539f-106">Některé z těchto vlastností mají podobné funkce nebo stejné.</span><span class="sxs-lookup"><span data-stu-id="2539f-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="2539f-107">Řádky v tabulce zobrazit skupiny vlastností, které provádí stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="2539f-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="2539f-108">Tyto vlastnosti můžete použít k přizpůsobení záhlaví sloupců v <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="2539f-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="2539f-109">Pořadí priorit pro souvisejících vlastností je zprava doleva, kde vlastnost ve sloupci nejvíce vpravo má nejvyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="2539f-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="2539f-110">Například pokud <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> je nastavený na <xref:System.Windows.Controls.GridViewColumnHeader> objektu a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> je nastavený na přidruženého <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> přednost.</span><span class="sxs-lookup"><span data-stu-id="2539f-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="2539f-111">V tomto scénáři <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="2539f-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="2539f-112">**Souvisejících vlastností pro záhlaví sloupců v GridView**</span><span class="sxs-lookup"><span data-stu-id="2539f-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="2539f-113">**Třídy**</span><span class="sxs-lookup"><span data-stu-id="2539f-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="2539f-114">**Vlastnosti místní nabídky**</span><span class="sxs-lookup"><span data-stu-id="2539f-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="2539f-115">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="2539f-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="2539f-116">**ToolTip**</span><span class="sxs-lookup"><span data-stu-id="2539f-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="2539f-117">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="2539f-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="2539f-118">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="2539f-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="2539f-119">**Šablona záhlaví**</span><span class="sxs-lookup"><span data-stu-id="2539f-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="2539f-120">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="2539f-120">**Properties**</span></span>|<span data-ttu-id="2539f-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="2539f-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="2539f-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="2539f-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="2539f-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="2539f-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="2539f-124">**Vlastnosti stylu**</span><span class="sxs-lookup"><span data-stu-id="2539f-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="2539f-125"><sup>1</sup>pro **vlastnosti šablony záhlaví**, pokud jste nastavili šablonu a vlastnosti pro výběr šablony, přednost šablony vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2539f-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="2539f-126">Nastavíte-li například <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost má přednost před.</span><span class="sxs-lookup"><span data-stu-id="2539f-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2539f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2539f-127">See Also</span></span>  
 [<span data-ttu-id="2539f-128">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2539f-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="2539f-129">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="2539f-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="2539f-130">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="2539f-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
