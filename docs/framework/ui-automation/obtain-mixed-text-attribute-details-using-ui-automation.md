---
title: "Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9dc823103d062d8165f3aae3f8cd49ad350cc2ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="17749-102">Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="17749-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="17749-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="17749-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="17749-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="17749-105">Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k získání podrobných informací o atributech text z textu oblast, která přesahuje více hodnot atributů.</span><span class="sxs-lookup"><span data-stu-id="17749-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="17749-106">Rozsah text se může shodovat se aktuální umístění pomocí kurzoru (nebo degenerovaný výběr) v dokumentu, souvislý výběr textu, kolekce výběrů nesouvislý textu nebo celý textový obsah dokumentu.</span><span class="sxs-lookup"><span data-stu-id="17749-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17749-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="17749-107">Example</span></span>  
 <span data-ttu-id="17749-108">Následující příklad kódu ukazuje, jak získat <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z rozsahu text kde <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> vrátí <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> objektu.</span><span class="sxs-lookup"><span data-stu-id="17749-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="17749-109"><xref:System.Windows.Automation.TextPattern> Vzor ovládacích prvků v kombinaci s <xref:System.Windows.Automation.Text.TextPatternRange> třídy, podporuje základní text atributy, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="17749-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="17749-110">Pro funkci specifické pro ovládací prvek, který není podporován nástrojem <xref:System.Windows.Automation.TextPattern> nebo <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> třída poskytuje metody pro klienty automatizace uživatelského rozhraní pro přístup k odpovídající nativní objekt modelu.</span><span class="sxs-lookup"><span data-stu-id="17749-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17749-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="17749-111">See Also</span></span>  
 [<span data-ttu-id="17749-112">Přehled prvku TextPattern automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="17749-113">Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="17749-114">Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="17749-115">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="17749-116">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="17749-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="17749-117">Získání textových atributů s použitím automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="17749-117">Obtain Text Attributes Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
