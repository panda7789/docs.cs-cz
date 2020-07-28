---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku tabulka v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní ITableProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168242"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider> , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.TablePattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků. Podřízené objekty tohoto elementu musí být implementovány <xref:System.Windows.Automation.Provider.ITableItemProvider> a uspořádány do dvojrozměrného logického systému souřadnic, který lze procházet podle řádků a sloupců. Tento vzor řízení je podobný <xref:System.Windows.Automation.Provider.IGridProvider> , s rozlišením, že jakékoli implementující ovládací prvky <xref:System.Windows.Automation.Provider.ITableProvider> musí také zveřejnit vztah záhlaví sloupce nebo řádku pro každý podřízený element. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku tabulka si všimněte následujících pokynů a konvencí:  
  
- Přístup k obsahu jednotlivých buněk provádí dvourozměrný logický souřadnicový systém nebo pole poskytované požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridProvider> .  
  
- Záhlaví sloupce nebo řádku může být obsaženo v objektu tabulky nebo se jedná o samostatný objekt záhlaví, který je spojen s objektem tabulky.  
  
- Záhlaví sloupců a řádků můžou zahrnovat primární hlavičku i všechny podpůrné hlavičky.  
  
> [!NOTE]
> Tento koncept bude zřejmý v tabulce aplikace Microsoft Excel, kde uživatel definoval sloupec "first name" (křestní jméno). Tento sloupec má teď dvě hlavičky – záhlaví "křestní jméno" definované uživatelem a alfanumerické označení pro daný sloupec přiřazenou aplikací.  
  
- V tématu [implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md) pro související funkce mřížky.  
  
 ![Tabulka se složitými položkami záhlaví](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Příklad tabulky se složitými záhlavími sloupců  
  
 ![Tabulka s nejednoznačnou vlastností RowOrColumnMajor](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Příklad tabulky s nejednoznačnou vlastností RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a>Vyžadovaná členové pro ITableProvider  
 Pro rozhraní ITableProvider jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Žádné|  
  
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
