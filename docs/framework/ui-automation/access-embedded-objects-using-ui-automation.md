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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: dc6426276d354dc3334013235cda45df8e7bb383
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408730"
---
# <a name="access-embedded-objects-using-ui-automation"></a>Přístup k vloženým objektům s použitím automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma ukazuje, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] můžete použít k vystavení objektů vloženým do ovládacího prvku typu textový obsah.  
  
> [!NOTE]
>  Vložené objekty mohou obsahovat bitové kopie, hypertextové odkazy, tlačítka, tabulky nebo ovládací prvky ActiveX.  
  
 Vložené objekty se považují za podřízené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele. To umožňuje, aby zpřístupnit prostřednictvím stejná struktura stromu automatizace uživatelského rozhraní jako všechny ostatní [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy. Funkce, pak je k dispozici prostřednictvím vzory ovládacích prvků, který je obvykle vyžaduje typ ovládacího prvku vložené objekty (například vzhledem k tomu, že jsou hypertextové odkazy založený na textu se podporují <xref:System.Windows.Automation.TextPattern>).  
  
 ![Vložené objekty v zásobníku textu. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Ukázka dokument s textový obsah, ("Věděli jste,?" ...) a dvě vložené objekty (obrázek velryba a hypertextový odkaz text), používá jako cíl pro příklady kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak načíst prostřednictvím kolekce vložené objekty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele. Dva objekty pro ukázkové dokumentu součástí zavedení by být vrácen (element bitové kopie a textový element).  
  
> [!NOTE]
>  Element obrázku by měl mít některé vnitřní text související s ním, který popisuje bitovou kopii, obvykle v jeho <xref:System.Windows.Automation.AutomationElement.NameProperty> (například "blue velryba."). Ale když se získávají rozsah textu pokrývání uzlů objekt bitovou kopii, bitovou kopii, ani tento popisný text se vrátí do proudu textu.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak získat rozsah textu z vložený objekt v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text zprostředkovatele. Rozsah text načíst je prázdného rozsahu kde výchozí koncový bod odpovídá "... oceánu. (místo) "a koncová koncový bod předchází ukončovací". "představující embedded hypertextový odkaz (jak je uvedeno image poskytnutou v úvodu). I když je to prázdného rozsahu, degenerovanou rozsah se nepovažuje, protože obsahuje nenulovou rozpětí.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> můžete načíst založený na textu vložený objekt například hypertextový odkaz; ale sekundární <xref:System.Windows.Automation.TextPattern> bude mít ho získat od vložený objekt vystavit plnou funkčnost.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled prvku TextPattern automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Přidání obsahu textového pole s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Hledání a zvýrazňování textu s použitím automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
