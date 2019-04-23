---
title: Získání textových atributů s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: d4cb9d12e4e2d5a28744e3a238884616a6db8f68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214894"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="0e11d-102">Získání textových atributů s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="0e11d-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e11d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0e11d-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="0e11d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0e11d-105">Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k získání textových atributů z rozsah textu.</span><span class="sxs-lookup"><span data-stu-id="0e11d-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="0e11d-106">Rozsah textu může odpovídat aktuální umístění blikajícího kurzoru (nebo degenerovanou výběr) v rámci dokumentu, souvislý výběr textu, kolekce nesouvislý textů nebo celý textový obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0e11d-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e11d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e11d-107">Example</span></span>  
 <span data-ttu-id="0e11d-108">Následující příklad kódu ukazuje, jak získat <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z rozsah textu.</span><span class="sxs-lookup"><span data-stu-id="0e11d-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="0e11d-109"><xref:System.Windows.Automation.TextPattern> – Vzor ovládacích prvků, v kombinaci s částí <xref:System.Windows.Automation.Text.TextPatternRange> třídy, podporuje základní text atributy, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="0e11d-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="0e11d-110">Pro konkrétní správu funkce, která není podporována produktem <xref:System.Windows.Automation.TextPattern> nebo <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, třída poskytuje metody pro klienty automatizace uživatelského rozhraní pro přístup k odpovídající nativní objekt modelu.</span><span class="sxs-lookup"><span data-stu-id="0e11d-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e11d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e11d-111">See also</span></span>

- [<span data-ttu-id="0e11d-112">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="0e11d-113">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="0e11d-114">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="0e11d-115">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0e11d-116">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="0e11d-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0e11d-117">Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e11d-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
