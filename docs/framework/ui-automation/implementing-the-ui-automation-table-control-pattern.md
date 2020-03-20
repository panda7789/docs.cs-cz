---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180120"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ITableProvider>konvence pro implementaci , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor <xref:System.Windows.Automation.TablePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků. Podřízené položky tohoto <xref:System.Windows.Automation.Provider.ITableItemProvider> prvku musí implementovat a uspořádat do dvojrozměrného logického souřadnicového systému, který lze procházet řádek a sloupec. Tento vzor ovládacího prvku <xref:System.Windows.Automation.Provider.IGridProvider>je obdobou , s <xref:System.Windows.Automation.Provider.ITableProvider> rozdílem, že všechny implementující ovládací prvek musí také vystavit sloupec nebo řádek záhlaví vztah pro každý podřízený prvek. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku tabulka, poznamenejte si následující pokyny a konvence:  
  
- Přístup k obsahu jednotlivých buněk je prostřednictvím dvourozměrného logického souřadnicového systému nebo pole poskytovaného požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
- Záhlaví sloupce nebo řádku může být obsaženo v objektu tabulky nebo může být samostatným objektem záhlaví, který je přidružen k objektu tabulky.  
  
- Záhlaví sloupců a řádků mohou obsahovat primární záhlaví i podpůrná záhlaví.  
  
> [!NOTE]
> Tento koncept se projeví v tabulce aplikace Microsoft Excel, kde uživatel definoval sloupec Křestní jméno. Tento sloupec má nyní dvě záhlaví – záhlaví "Jméno" definované uživatelem a alfanumerické označení pro tento sloupec přiřazené aplikací.  
  
- Informace o souvisejících funkcích mřížky naleznete [v tématu Implementace vzoru řízení mřížky automatizace](implementing-the-ui-automation-grid-control-pattern.md) uživatelského rozhraní.  
  
 ![Tabulka se složitými položkami záhlaví.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Příklad tabulky se složitými záhlavími sloupců  
  
 ![Tabulka s nejednoznačným vlastnostem RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Příklad tabulky s nejednoznačnou vlastností RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>Požadované členy pro ITableProvider  
 Pro rozhraní ITableProvider jsou vyžadovány následující vlastnosti a metody.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacího prvku nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
