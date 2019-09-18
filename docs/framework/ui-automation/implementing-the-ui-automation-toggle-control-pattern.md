---
title: Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: a9b03fbffc4e922cb3d00738e8df00fc0393b799
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043139"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>Implementace vzoru ovládacích prvků přepínání pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IToggleProvider>implementaci, včetně informací o metodách a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.TogglePattern> ovládacího prvku slouží k podpoře ovládacích prvků, které mohou procyklovat sadu stavů a udržovat stav po jeho nastavení. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku přepínací tlačítko si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky, které neudržují stav při aktivaci, jako jsou tlačítka, tlačítka panelu nástrojů a hypertextové <xref:System.Windows.Automation.Provider.IInvokeProvider> odkazy, musí implementovat místo toho.  
  
- Ovládací prvek musí procyklovat <xref:System.Windows.Automation.ToggleState> v následujícím pořadí <xref:System.Windows.Automation.ToggleState.Off> : <xref:System.Windows.Automation.ToggleState.On>a, je-li to podporováno <xref:System.Windows.Automation.ToggleState.Indeterminate>,.  
  
- <xref:System.Windows.Automation.TogglePattern>neposkytuje metodu setstate (newState), protože došlo k problémům s přímým nastavením zaškrtávacího políčka se stavem Tri bez nutnosti absolvovat příslušné <xref:System.Windows.Automation.ToggleState> pořadí.  
  
- Ovládací prvek RadioButton neimplementuje <xref:System.Windows.Automation.Provider.IToggleProvider>, protože není schopen cyklicky předávat své platné stavy.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>Vyžadovaná členové pro IToggleProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.IToggleProvider>jsou vyžadovány následující vlastnosti a metody.  
  
|Povinný člen|Typ člena|Poznámky|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Vlastnost|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacího prvku nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Zjištění stavu přepnutí zaškrtávacího políčka pomocí automatizace uživatelského rozhraní](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
