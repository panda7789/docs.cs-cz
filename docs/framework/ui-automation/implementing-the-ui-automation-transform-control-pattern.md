---
title: Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzorového ovládacího prvku transformace v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní ITransformProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: da11ce4cf9da10c0ebb990f9439b0bbe3621c561
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168218"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementace vzoru ovládacích prvků transformace pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITransformProvider> , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 <xref:System.Windows.Automation.TransformPattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které lze přesunout, změnit jeho velikost nebo otočit v dvojrozměrném prostoru. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzorového ovládacího prvku transformace si všimněte následujících pokynů a konvencí:  
  
- Podpora tohoto vzoru ovládacího prvku není omezena na objekty na ploše. Tento vzor ovládacího prvku musí být také podporován podřízenými objekty kontejneru, pokud lze podřízené objekty přesunout, změnit jejich velikost nebo otáčet volně v rámci hranic kontejneru.  
  
- Objekt nelze přesunout, změnit jeho velikost nebo otočit tak, že jeho výsledná poloha obrazovky by byla zcela mimo souřadnice kontejneru, a proto nebude přístupná k klávesnici nebo myši (například při přesunutí okna nejvyšší úrovně mimo hranice zobrazení kontejneru), v případě, že se přesune okno na nejvyšší úrovni. V těchto případech je objekt umístěn co nejblíže požadovaným souřadnicím obrazovky nahoře nebo vlevo přepsané, aby byly v rámci hranic kontejneru.  
  
- U systémů s více monitory, pokud je objekt přesunutý, mění jeho velikost nebo se úplně otáčí mimo kombinaci souřadnic desktopové obrazovky, objekt se umístí na primární monitor co nejblíže požadovaným souřadnicím.  
  
- Všechny parametry a hodnoty vlastností jsou absolutní a nezávisle na národním prostředí.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>Vyžadovaná členové pro ITransformProvider  
 Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.ITransformProvider> .  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> – Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> je hodnota false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> – Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> je hodnota false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> – Pokud <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> je hodnota false.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
