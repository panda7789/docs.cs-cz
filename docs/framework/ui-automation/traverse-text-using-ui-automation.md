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
ms.openlocfilehash: 71df7c8f9dde388ffc4445389e105a4ad686539f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441873"
---
# <a name="traverse-text-using-ui-automation"></a>Procházení textu s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V tomto tématu se dozvíte, jak pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] procházet textový obsah dokumentu tím, že <xref:System.Windows.Automation.Text.TextUnit> zvýší.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak procházet obsah poskytovatele textu automatizace uživatelského rozhraní. Metoda <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncových bodů <xref:System.Windows.Automation.Text.TextPatternRange>. Tento rozsah textu je typicky negenerovaný rozsah reprezentující textový kurzor.  
  
> [!NOTE]
> Vzhledem k tomu, že pouze textové vložené objekty jsou považovány za součást textového streamu, vložené objekty, jako jsou obrázky, neovlivní `Move` nebo její návratovou hodnotu.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Jakákoli metoda využívající <xref:System.Windows.Automation.Text.TextUnit> se odloží k nejbližšímu největšímu <xref:System.Windows.Automation.Text.TextUnit>, který je podporován, pokud daný <xref:System.Windows.Automation.Text.TextUnit> není podporován ovládacím prvkem.  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](ui-automation-textpattern-overview.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](find-and-highlight-text-using-ui-automation.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
