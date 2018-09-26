---
title: Procházení textu s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 3b28876106205f7b13f8609c7a1e3bb0a6548cce
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087941"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="ad707-102">Procházení textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad707-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="ad707-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad707-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ad707-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ad707-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ad707-105">Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k procházení textový obsah dokument <xref:System.Windows.Automation.Text.TextUnit> přírůstky.</span><span class="sxs-lookup"><span data-stu-id="ad707-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad707-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad707-106">Example</span></span>  
 <span data-ttu-id="ad707-107">Následující příklad kódu ukazuje, jak procházet obsah textu zprostředkovatele automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ad707-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="ad707-108"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Metoda přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="ad707-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="ad707-109">Tento rozsah textu je obvykle degenerovanou rozsah reprezentující kurzor.</span><span class="sxs-lookup"><span data-stu-id="ad707-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad707-110">Od té doby pouze textové vložené objekty jsou považovány za součást textového datového proudu, vložené objekty, jako jsou obrázky nemají vliv na `Move` nebo jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ad707-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="ad707-111">Každá metoda používající <xref:System.Windows.Automation.Text.TextUnit> bude odložit na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované if daný <xref:System.Windows.Automation.Text.TextUnit> není podporována ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="ad707-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad707-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad707-112">See Also</span></span>  
 [<span data-ttu-id="ad707-113">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad707-113">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="ad707-114">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad707-114">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="ad707-115">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad707-115">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="ad707-116">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad707-116">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="ad707-117">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="ad707-117">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
