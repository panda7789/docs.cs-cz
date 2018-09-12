---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 7466a7cc25ac742483e21fc1ee4a631bd43bc5a3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699420"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider>, včetně informací o vlastnosti, metody a události. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.TablePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které fungují jako kontejnery pro kolekci podřízených elementů. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ITableItemProvider> a uspořádané v dvojrozměrné logické systém souřadnic, který můžete procházet podle řádků a sloupců. Tento vzor ovládacích prvků je obdobou <xref:System.Windows.Automation.Provider.IGridProvider>, s rozlišovat, že žádné řídicí implementace <xref:System.Windows.Automation.Provider.ITableProvider> musí vystavit také sloupec nebo řádek záhlaví vztah pro každý podřízený prvek. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků tabulka, mějte na paměti následující pokyny a konvence:  
  
-   Přístup k obsahu jednotlivých buněk je dvojrozměrné logické souřadnicový systém nebo pole poskytované vyžaduje souběžné provádění <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Sloupec nebo řádek záhlaví mohou být obsaženy v rámci objektu tabulky nebo být samostatné hlavičkové objekt, který je přidružený objekt tabulky.  
  
-   Záhlaví řádků a sloupců může obsahovat hlavičku primární i podpůrné záhlaví.  
  
> [!NOTE]
>  Tento koncept se stane zřejmé ve [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] tabulky, kde má uživatelem definovaný sloupce "Jméno". Tento sloupec obsahuje teď dvě záhlaví – hlavička "Jméno" definované uživatelem a alfanumerické označení pro tento sloupec přiřazené aplikace.  
  
-   Zobrazit [implementace vzoru ovládacích prvků mřížka automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) pro funkci související mřížce.  
  
 ![Tabulka s položkami complex – hlavička ](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Příklad tabulky se záhlavími sloupců komplexní  
  
 ![Tabulka s nejednoznačnou vlastnost RowOrColumnMajor. ](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Příklad tabulky s vlastností nejednoznačný RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Požadované členy pro ITableProvider  
 Následující vlastnosti a metody jsou požadovány pro ITableProvider rozhraní.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Žádné|  
  
 Tento model ovládací prvek nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Tento model ovládací prvek nemá žádné související výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
