---
title: Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6216c8daa183db28cf5f127fddac0e8f4583d370
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Získání podrobných informací o smíšených textových atributech s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak používat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k získání podrobných informací o atributech text z textu oblast, která přesahuje více hodnot atributů. Rozsah text se může shodovat se aktuální umístění pomocí kurzoru (nebo degenerovaný výběr) v dokumentu, souvislý výběr textu, kolekce výběrů nesouvislý textu nebo celý textový obsah dokumentu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak získat <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z rozsahu text kde <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> vrátí <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> objektu.  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> Vzor ovládacích prvků v kombinaci s <xref:System.Windows.Automation.Text.TextPatternRange> třídy, podporuje základní text atributy, vlastnosti a metody. Pro funkci specifické pro ovládací prvek, který není podporován nástrojem <xref:System.Windows.Automation.TextPattern> nebo <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> třída poskytuje metody pro klienty automatizace uživatelského rozhraní pro přístup k odpovídající nativní objekt modelu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Získání textových atributů s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
