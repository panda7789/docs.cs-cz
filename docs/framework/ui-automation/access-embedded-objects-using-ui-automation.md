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
ms.openlocfilehash: 07223b9e48905b0952e37a6acdb703f584d166d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131245"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] lze použít ke zveřejnění objekty vložené v obsahu prvku textu.  
  
> [!NOTE]
>  Vložené objekty mohou obsahovat obrázky, hypertextové odkazy, tlačítka, tabulek nebo ovládací prvky ActiveX.  
  
 Vložené objekty jsou považovány za podřízené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu. To jim zpřístupní prostřednictvím stejnou strukturu stromu automatizace uživatelského rozhraní jako všechny ostatní umožňuje [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy. Funkce, pak je k dispozici prostřednictvím vzorů ovládacích prvků, které jsou obvykle vyžaduje vložené objekty – typ ovládacího prvku (například protože hypertextové odkazy jsou založeny na text se bude podporovat <xref:System.Windows.Automation.TextPattern>).  
  
 ![Vložené objekty v zásobník textu. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Ukázkový dokument s textový obsah ("Věděli jste?" ...) a dvě vložené objekty (obrázek velryba a text hypertextového odkazu), použít jako cíl pro příklady kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak načíst kolekce vložené objekty v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu. Pro ukázkový dokument v úvodu k dispozici bude vrácen dva objekty (image element a textový element).  
  
> [!NOTE]
>  Elementu obrázku by měl mít některé vnitřní text související s tím, který popisuje bitovou kopii, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "modrá velryba."). Ale při se získá rozsah textu pokrývání uzlů objektu image, image ani tento popisný text se vrací do toku textu.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak získat rozsah textu z vloženého objektu v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele textu. Rozsah textu, načíst je prázdného rozsahu, kde výchozí koncový bod odpovídá "... na oceánských. (místo) "a koncové koncový bod předchází uzavírací". "představující embedded hypertextový odkaz (jak je uvedeno na obrázku v úvodu k dispozici). I když je to prázdný rozsah, to se nepovažuje za degenerovanou rozsah vzhledem k tomu, že má nenulovou rozpětí.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> můžete načíst textový vložený objekt například hypertextový odkaz. ale sekundární <xref:System.Windows.Automation.TextPattern> muset získat z vloženého objektu vystavit plnou funkčnost.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
