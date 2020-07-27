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
# <a name="traverse-text-using-ui-automation"></a>Procházení textu s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 V tomto tématu se dozvíte, jak pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] přírůstků procházet textový obsah dokumentu <xref:System.Windows.Automation.Text.TextUnit> .  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak procházet obsah poskytovatele textu automatizace uživatelského rozhraní. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>Metoda přesune <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncové body a <xref:System.Windows.Automation.Text.TextPatternRange> . Tento rozsah textu je typicky negenerovaný rozsah reprezentující textový kurzor.  
  
> [!NOTE]
> Vzhledem k tomu, že pouze textové vložené objekty jsou považovány za součást textového streamu, vložené objekty, jako jsou obrázky, neovlivňují `Move` nebo vracejí hodnotu.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Jakékoli metody využívající <xref:System.Windows.Automation.Text.TextUnit> se budou odkládat na další největší <xref:System.Windows.Automation.Text.TextUnit> podporovanou hodnotu, pokud daný <xref:System.Windows.Automation.Text.TextUnit> ovládací prvek není podporován.  
  
## <a name="see-also"></a>Viz také

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](ui-automation-textpattern-overview.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](find-and-highlight-text-using-ui-automation.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
