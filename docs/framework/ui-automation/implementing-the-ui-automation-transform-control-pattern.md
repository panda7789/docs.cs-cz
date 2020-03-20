---
title: Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: 5643bc85972ea33cc31b1a83ecf7615dbb275bc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180043"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ITransformProvider>konvence pro implementaci , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.TransformPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které lze přesunout, změnit jejich velikost nebo otočit v rámci dvourozměrného prostoru. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku transformace, poznamenejte si následující pokyny a konvence:  
  
- Podpora tohoto vzoru ovládacího prvku není omezena na objekty na ploše. Tento vzor ovládacího prvku musí být také podporovánpodřízenými objekty kontejneru, pokud podřízené objekty lze přesunout, změnit velikost nebo volně otáčet v rámci hranic kontejneru.  
  
- Objekt nelze přesunout, změnit jejich velikost nebo otočit tak, aby jeho výsledné umístění obrazovky bylo zcela mimo souřadnice jeho kontejneru, a proto nepřístupné pro klávesnici nebo myš (například když je okno nejvyšší úrovně přesunuto mimo obrazovku nebo podřízený objekt se přesune mimo hranice výřezu kontejneru). V těchto případech je objekt umístěn co nejblíže k požadovaným souřadnicím obrazovky, jak je to možné s horní nebo levé souřadnice přepsány být v rámci hranice kontejneru.  
  
- U systémů s více monitory je objekt přesunut, změnit jejich velikost nebo otočení zcela mimo kombinované souřadnice obrazovky plochy, objekt je umístěn na primárnímonitor co nejblíže požadovaným souřadnicím.  
  
- Všechny parametry a hodnoty vlastností jsou absolutní a nezávislé na národním prostředí.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>Požadované členy pro ITransformProvider  
 Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.ITransformProvider>vyžadovány pro implementaci .  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> - Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> je to nepravdivé.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> - Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> je to nepravdivé.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> - Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> je to nepravdivé.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
