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
ms.openlocfilehash: c338f858f1715d23cad96919db4a21a6ba49710f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446909"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>Získání textových atributů s použitím automatizace uživatelského rozhraní
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range. A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.  
  
## <a name="example"></a>Příklad  
 The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods. For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](ui-automation-textpattern-overview.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](find-and-highlight-text-using-ui-automation.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní](obtain-mixed-text-attribute-details-using-ui-automation.md)
