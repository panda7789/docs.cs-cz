---
title: Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: c9199e0ea1971c22bfc1f6334b9d2d9d73bb048c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435053"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementace vzoru ovládacích prvků MultipleView pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Model ovládacího prvku <xref:System.Windows.Automation.MultipleViewPattern> slouží k podpoře ovládacích prvků, které poskytují a jsou schopny přepínat mezi různými reprezentacemi stejné sady informací nebo podřízených ovládacích prvků.  
  
 Příklady ovládacích prvků, které mohou prezentovat více zobrazení, zahrnují zobrazení seznamu (které může zobrazit jeho obsah jako miniatury, dlaždice, ikony nebo podrobnosti), grafy aplikace Microsoft Excel (výseč, čára, pruh, hodnota buňky se vzorcem), dokumenty aplikace Microsoft Word (normální, rozložení na webu, tisk rozložení, rozložení pro čtení, osnova), Microsoft Outlook kalendář (year, month, Week, Day) a Microsoft Windows Media Player skiny. Podporovaná zobrazení jsou určena vývojářem ovládacího prvku a jsou specifická pro každý ovládací prvek.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci modelu více ovládacích prvků zobrazení si všimněte následujících pokynů a konvencí:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider> by měl být implementován také v kontejneru, který spravuje aktuální zobrazení, pokud se liší od ovládacího prvku, který poskytuje aktuální zobrazení. Například Průzkumník Windows obsahuje ovládací prvek seznamu pro aktuální obsah složky, zatímco zobrazení pro ovládací prvek je spravováno z aplikace Průzkumník Windows.  
  
- Ovládací prvek, který je schopný seřadit jeho obsah, není považován za podporu více zobrazení.  
  
- Kolekce zobrazení musí být identická mezi instancemi.  
  
- Názvy zobrazení musí být vhodné pro použití v Převod textu na řeč, Braillova písma a dalších aplikacích čitelných lidmi.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Vyžadovaná členové pro IMultipleViewProvider  
 Pro implementaci IMultipleViewProvider jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Žádné|  
  
 K tomuto vzoru ovládacích prvků nejsou přidruženy žádné události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatel musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Když je volána buď <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>, nebo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> parametr, který není členem podporované kolekce zobrazení.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
