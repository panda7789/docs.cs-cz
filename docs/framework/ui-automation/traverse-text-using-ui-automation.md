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
ms.openlocfilehash: d73ae4ca11d6f5417bb5cb768eae4e586538bd92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154788"
---
# <a name="traverse-text-using-ui-automation"></a>Procházení textu s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k procházení textový obsah dokument <xref:System.Windows.Automation.Text.TextUnit> přírůstky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak procházet obsah textu zprostředkovatele automatizace uživatelského rozhraní. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Metoda přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body <xref:System.Windows.Automation.Text.TextPatternRange>. Tento rozsah textu je obvykle degenerovanou rozsah reprezentující kurzor.  
  
> [!NOTE]
>  Od té doby pouze textové vložené objekty jsou považovány za součást textového datového proudu, vložené objekty, jako jsou obrázky nemají vliv na `Move` nebo jeho návratovou hodnotu.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Každá metoda používající <xref:System.Windows.Automation.Text.TextUnit> bude odložit na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované if daný <xref:System.Windows.Automation.Text.TextUnit> není podporována ovládacím prvkem.  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
