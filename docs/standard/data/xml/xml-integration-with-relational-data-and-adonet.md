---
title: "XML integrace s relačních dat a ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d03a0ca7518b06c08d98967d7c5ae864f1c04ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>XML integrace s relačních dat a ADO.NET
**XmlDataDocument** třída je třídu odvozenou z **třídou XMLDocument nastavenou na**a obsahuje XML data. Výhodou **XmlDataDocument** je, že zajišťuje most mezi hierarchické a relační data. Je **třídou XMLDocument nastavenou na** mohou být vázány na **datovou sadu** a obě třídy můžete synchronizovat změny provedené data obsažená ve dvou tříd. **Třídou XMLDocument nastavenou na** která je vázaná **datovou sadu** umožňuje XML tak, aby integrovat relačních dat, a není nutné mít data reprezentována jako buď XML nebo v relačním formátu. Můžete provést i a nesmí být omezené na jednom znázornění dat.  
  
 Výhod, které nejsou k dispozici ve dvou zobrazení data jsou:  
  
-   Strukturované část dokumentu XML lze mapovat na datovou sadu a efektivně ukládat, indexované a vyhledávat.  
  
-   Transformace, ověřování a navigační lze provést efektivně prostřednictvím modelu kurzoru přes data XML, která je uložená relationally. V některých případech je možné ji provést efektivněji proti relační struktury než pokud XML je uložen v **třídou XMLDocument nastavenou na** modelu.  
  
-   **Datovou sadu** můžete uložit část XML. To znamená, že můžete použít **XPath** nebo **XslTransform** k uložení do **datovou sadu** pouze elementy a atributy, které vás zajímají. Odtud můžete provedeny změny menší, která jsou filtrovaná podmnožinu dat, se změnami šíření větší data ve **XmlDataDocument**.  
  
 Můžete taky spustit transformace přes data, která byla načtena do **datovou sadu** ze serveru SQL Server. Další možností je vytvořit vazbu WinForm spravované styl třídy rozhraní .NET Framework a pro ovládací prvky webových formulářů **datovou sadu** , se naplní ze vstupní datový proud XML.  
  
 Vedle podpory **XslTransform**, **XmlDataDocument** zpřístupní relační data **XPath** dotazy a ověření.  V podstatě všechny XML služby jsou dostupné přes relačních dat a relační zařízení, jako je vazba ovládacího prvku, codegen atd., jsou k dispozici prostřednictvím strukturovaných projekce XML bez kompromisů věrnosti XML.  
  
 Protože **XmlDataDocument** je zděděn z **třídou XMLDocument nastavenou na**, poskytuje implementaci W3C modelu DOM. Fakt, **XmlDataDocument** je přidružen k nim a ukládá podmnožinu jeho data v rámci, **datovou sadu** neomezuje nebo změnit jeho použití jako **třídou XMLDocument nastavenou na** žádným způsobem. Kód zapisovaný využívat **třídou XMLDocument nastavenou na** funguje v nezměněném stavu proti **XmlDataDocument**. **Datovou sadu** poskytuje relační zobrazení dat tak, že definujete tabulek, sloupců, vztahy a omezení a je úložiště dat, které uživatel samostatnou, v paměti.  
  
 Následující obrázek znázorňuje jiné přidružení, že má XML data s **datovou sadu** a **XmlDataDocument**.  
  
 ![Datová sada XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 Na obrázku vidíte, že je možné načíst XML data přímo do **datovou sadu**, což umožňuje přímé manipulaci se souborem XML relační způsobem. Nebo, XML, je možné načíst do odvozené třídy modelu DOM, který je **XmlDataDocument**a následně načíst a synchronizována s **datovou sadu**. Protože **datovou sadu** a **XmlDataDocument** jsou synchronizovány v rámci jedné sady dat, se projeví změny provedené v datech v jedno úložiště v jiného úložiště.  
  
 **XmlDataDocument** dědí všechny úpravy a navigační funkce z **třídou XMLDocument nastavenou na**. V určitých časech při použití **XmlDataDocument** a jeho zděděné funkce synchronizovat se službou **datovou sadu**, je vhodnější možnost než načtení XML přímo do **datovou sadu**. V následující tabulce jsou uvedeny položky, které mají být považovány za při výběru, kterou metodu použít k načtení **datovou sadu**.  
  
|Pokud k načtení XML přímo do datové sady|Při synchronizaci XmlDataDocument s datové sady|  
|----------------------------------------------|-----------------------------------------------------------|  
|Dotazy dat v **datovou sadu** se snadněji pomocí SQL než XPath.|Dotazy XPath jsou potřeba nad daty v **datovou sadu**.|  
|Zachování elementu řazení ve zdroji XML není důležité.|Zachování elementu řazení ve zdroji XML je velmi důležité.|  
|Mezer mezi elementy a formátování nemusí být zachována ve zdroji XML.|Prázdné znaky a formátování zachovávání ve zdroji XML je velmi důležité.|  
  
 Pokud načtení a zápis XML přímo do a z **datovou sadu** adresy vašim potřebám, najdete v části [načítání datové sady z XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápis datovou sadu jako XML Data](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Pokud načítání **datovou sadu** z **XmlDataDocument** adresy vašim potřebám, najdete v části [synchronizace Datasetwith dokument XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Viz také  
 [Pomocí XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
