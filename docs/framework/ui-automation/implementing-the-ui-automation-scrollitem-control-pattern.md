---
title: Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: e8f9373c840b00c8089f01a562f768f27f2cd945
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043305"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementace vzoru ovládacích prvků ScrollItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IScrollItemProvider>nástroje, včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IScrollProvider>. <xref:System.Windows.Automation.ScrollItemPattern> Tento model ovládacího prvku funguje jako komunikační kanál mezi podřízeným ovládacím prvkem a jeho kontejnerem, aby bylo zajištěno, že kontejner může měnit aktuálně viditelný obsah (nebo oblast) v jeho zobrazení, aby zobrazil podřízený ovládací prvek. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku položka posouvání si všimněte následujících pokynů a konvencí:  
  
- K implementaci rozhraní IScrollItemProvider nejsou vyžadovány položky obsažené v ovládacím prvku okna nebo plátno. Jako alternativu však musí zveřejnit platné umístění pro <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Tím umožníte, aby klientská aplikace pro automatizaci <xref:System.Windows.Automation.ScrollPattern> uživatelského rozhraní používala metody vzoru ovládacího prvku na kontejneru, aby zobrazila podřízenou položku.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Vyžadovaná členové pro IScrollItemProvider  
 Následující metoda je vyžadována pro implementaci rozhraní IScrollProvider.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Method|Žádné|  
  
 Tento model řízení nemá žádné přidružené vlastnosti nebo události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Pokud se položka nedá posunout do zobrazení:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
