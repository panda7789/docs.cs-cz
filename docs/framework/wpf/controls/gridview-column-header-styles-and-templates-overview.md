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
ms.openlocfilehash: ad0f7cacc8256e060bb12611bd1818b694e1e6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="037d9-102">GridView Styly záhlaví sloupců a přehled šablon</span><span class="sxs-lookup"><span data-stu-id="037d9-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="037d9-103">Tento přehled popisuje pořadí priorit pro vlastnosti, které můžete použít k přizpůsobení v záhlaví sloupce <xref:System.Windows.Controls.GridView> režim zobrazení <xref:System.Windows.Controls.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="037d9-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="037d9-104">Přizpůsobení záhlaví sloupce v GridView</span><span class="sxs-lookup"><span data-stu-id="037d9-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="037d9-105">Vlastnosti, které definují obsah, rozvržení a stylu záhlaví sloupce v <xref:System.Windows.Controls.GridView> jsou k dispozici v mnoha související třídy.</span><span class="sxs-lookup"><span data-stu-id="037d9-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="037d9-106">Některé z těchto vlastností mají podobné funkce nebo stejné.</span><span class="sxs-lookup"><span data-stu-id="037d9-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="037d9-107">Řádky v tabulce zobrazit skupiny vlastností, které provádí stejnou funkci.</span><span class="sxs-lookup"><span data-stu-id="037d9-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="037d9-108">Tyto vlastnosti můžete použít k přizpůsobení záhlaví sloupců v <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="037d9-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="037d9-109">Pořadí priorit pro souvisejících vlastností je zprava doleva, kde vlastnost ve sloupci nejvíce vpravo má nejvyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="037d9-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="037d9-110">Například pokud <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> je nastavený na <xref:System.Windows.Controls.GridViewColumnHeader> objektu a <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> je nastavený na přidruženého <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> přednost.</span><span class="sxs-lookup"><span data-stu-id="037d9-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="037d9-111">V tomto scénáři <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="037d9-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="037d9-112">**Souvisejících vlastností pro záhlaví sloupců v GridView**</span><span class="sxs-lookup"><span data-stu-id="037d9-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="037d9-113">**Třídy**</span><span class="sxs-lookup"><span data-stu-id="037d9-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="037d9-114">**Vlastnosti místní nabídky**</span><span class="sxs-lookup"><span data-stu-id="037d9-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="037d9-115">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="037d9-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="037d9-116">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="037d9-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="037d9-117">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="037d9-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="037d9-118">Nelze použít</span><span class="sxs-lookup"><span data-stu-id="037d9-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="037d9-119">**Šablona záhlaví**</span><span class="sxs-lookup"><span data-stu-id="037d9-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="037d9-120">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="037d9-120">**Properties**</span></span>|<span data-ttu-id="037d9-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="037d9-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="037d9-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="037d9-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="037d9-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="037d9-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="037d9-124">**Vlastnosti stylu**</span><span class="sxs-lookup"><span data-stu-id="037d9-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="037d9-125"><sup>1</sup>pro **vlastnosti šablony záhlaví**, pokud jste nastavili šablonu a vlastnosti pro výběr šablony, přednost šablony vlastnost.</span><span class="sxs-lookup"><span data-stu-id="037d9-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="037d9-126">Nastavíte-li například <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vlastnost má přednost před.</span><span class="sxs-lookup"><span data-stu-id="037d9-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037d9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="037d9-127">See Also</span></span>  
 [<span data-ttu-id="037d9-128">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="037d9-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="037d9-129">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="037d9-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="037d9-130">Rutina GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="037d9-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
