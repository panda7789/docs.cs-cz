---
title: Procházení textu s použitím automatizace uživatelského rozhraní
description: Podívejte se na příklad, jak procházet textový obsah dokumentu pomocí automatizace uživatelského rozhraní Microsoft v TextUnit přírůstcích.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 0b4269d043fd6cd0cc5da9825714aab4ead701f9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168087"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="f6ff8-103">Procházení textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ff8-103">Traverse Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="f6ff8-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f6ff8-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f6ff8-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f6ff8-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f6ff8-106">V tomto tématu se dozvíte, jak pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] přírůstků procházet textový obsah dokumentu <xref:System.Windows.Automation.Text.TextUnit> .</span><span class="sxs-lookup"><span data-stu-id="f6ff8-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ff8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ff8-107">Example</span></span>  
 <span data-ttu-id="f6ff8-108">Následující příklad kódu ukazuje, jak procházet obsah poskytovatele textu automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6ff8-108">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="f6ff8-109"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>Metoda přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body a <xref:System.Windows.Automation.Text.TextPatternRange> .</span><span class="sxs-lookup"><span data-stu-id="f6ff8-109">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="f6ff8-110">Tento rozsah textu je typicky negenerovaný rozsah reprezentující textový kurzor.</span><span class="sxs-lookup"><span data-stu-id="f6ff8-110">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6ff8-111">Vzhledem k tomu, že pouze textové vložené objekty jsou považovány za součást textového streamu, vložené objekty, jako jsou obrázky, neovlivňují `Move` nebo vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6ff8-111">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="f6ff8-112">Jakékoli metody využívající <xref:System.Windows.Automation.Text.TextUnit> se budou odkládat na další největší <xref:System.Windows.Automation.Text.TextUnit> podporovanou hodnotu, pokud daný <xref:System.Windows.Automation.Text.TextUnit> ovládací prvek není podporován.</span><span class="sxs-lookup"><span data-stu-id="f6ff8-112">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ff8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ff8-113">See also</span></span>

- [<span data-ttu-id="f6ff8-114">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ff8-114">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="f6ff8-115">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ff8-115">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="f6ff8-116">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ff8-116">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="f6ff8-117">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ff8-117">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f6ff8-118">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="f6ff8-118">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
