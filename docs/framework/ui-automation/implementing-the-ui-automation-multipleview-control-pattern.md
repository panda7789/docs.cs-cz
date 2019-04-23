---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 74e5908dfcd42d031464ffccedb530be4a71a3f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125195"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, včetně informací o události a vlastnosti. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které poskytují a je možné přepínat mezi více reprezentací stejnou sadu informace nebo podřízené ovládací prvky.  
  
 Příklady ovládacích prvků, které mohou představovat několik zobrazení (které můžete zobrazit jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti) zobrazení seznamu [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafy (výsečového, řádek, pruhový, hodnota buňky pomocí vzorce), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumenty (normální, rozložení webové stránky Tisk rozložení, rozložení pro čtení, osnovy), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendáře (roku, měsíce, týdne, dne), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skinů v šablonách. Podporované zobrazení jsou určeno vývojářem ovládacího prvku a jsou specifické pro každý ovládací prvek.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci modelu řízení několika zobrazení, mějte na paměti následující pokyny a konvence:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> musí být provedeny také na kontejner, který spravuje aktuální zobrazení, pokud se liší od ovládací prvek, který poskytuje aktuální zobrazení. Průzkumník Windows například obsahuje ovládací prvek seznamu pro aktuální obsah složky, zatímco zobrazení pro ovládací prvek spravuje se z aplikace Průzkumník Windows.  
  
-   Ovládací prvek, který je možné seřadit její obsah se nepovažuje za pro podporu více zobrazení.  
  
-   Kolekce prvků View musí být identické napříč instancemi.  
  
-   Zobrazit názvy musí být vhodný pro použití v textu na řeč, Brailleových a dalších běžně čitelné aplikací.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Požadované členy pro IMultipleViewProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci IMultipleViewProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Žádné|  
  
 Nejsou žádné akce přidružené k této – vzor ovládacích prvků.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatel musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Když buď <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> nebo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> je volána s parametrem, který není členem kolekce podporované zobrazení.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
