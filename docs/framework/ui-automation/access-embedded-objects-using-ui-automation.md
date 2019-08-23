---
title: Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 83e54da5fdb75e3da44009ec700102d6bd7ae5e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937970"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma ukazuje, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jak lze použít k vystavení objektů vložených do obsahu ovládacího prvku text.  
  
> [!NOTE]
> Vložené objekty mohou obsahovat obrázky, hypertextové odkazy, tlačítka, tabulky nebo ovládací prvky ActiveX.  
  
 Vložené objekty jsou považovány za podřízené [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] objekty poskytovatele textu. To umožňuje zveřejnění prostřednictvím stejné struktury stromu pro automatizaci uživatelského rozhraní jako všechny ostatní [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky. Funkce jsou zase zpřístupněny prostřednictvím vzorů ovládacích prvků, které jsou obvykle vyžadovány typem ovládacího prvku vložené objekty (například protože hypertextové odkazy jsou založené na textu, <xref:System.Windows.Automation.TextPattern>budou podporovat).  
  
 ![Vložené objekty v textovém kontejneru.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Ukázkový dokument s textovým obsahem ("Víte, že víte?" ...) a dva vložené objekty (obrázek Whale a textový hypertextový odkaz) používané jako cíl pro příklady kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak načíst kolekci vložených objektů v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu. Pro ukázkový dokument poskytnutý v úvodu by se vracely dva objekty (element obrázku a textový element).  
  
> [!NOTE]
> K elementu Image by měl být přidružen nějaký vnitřní text, který popisuje obrázek, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "modrý Whale"). Pokud se ale Získá rozsah textu, který pokrývá objekt obrázku, nevrátí se do textového streamu ani obrázek ani tento popisný text.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak získat textovou oblast z vloženého objektu v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu. Načtený rozsah textu je prázdný rozsah, ve kterém následuje počáteční koncový bod... spadající. (Space) "a koncový bod předchází konci". "představující vložený hypertextový odkaz (jak znázorňuje obrázek uvedený v úvodu). I když se jedná o prázdný rozsah, není považován za negenerovaný rozsah, protože má nenulové rozpětí.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern>může načíst textový vložený objekt, jako je hypertextový odkaz. sekundární <xref:System.Windows.Automation.TextPattern> objekt se však bude muset získat z vloženého objektu, aby bylo možné zobrazit jeho plnou funkčnost.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
