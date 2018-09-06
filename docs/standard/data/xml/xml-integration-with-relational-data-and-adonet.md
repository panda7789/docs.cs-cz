---
title: Integrace XML s relačními daty a ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d86c590f2d5fe6bc970c2f8ac6de43d3e8485650
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877541"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integrace XML s relačními daty a ADO.NET
**XmlDataDocument** třída je odvozená třída **XmlDocument**a obsahuje XML data. Výhodou **XmlDataDocument** je, že umožňuje most mezi relačních a hierarchických dat. Je **XmlDocument** , který může být vázaný na **datovou sadu** a obě třídy se mohou synchronizovat změny pro data obsažená ve dvou tříd. **XmlDocument** , který je vázán na **datovou sadu** umožňuje XML k integraci s relačními daty a není nutné mít data reprezentována jako buď XML nebo v relačním formátu. Můžete mít obojí a nesmí být omezeny na jednoho znázornění dat.  
  
 Výhod, které nejsou k dispozici ve dvou zobrazení data jsou:  
  
-   Strukturované část dokumentu XML lze mapovat na datovou sadu a efektivně uloženy, indexovat a prohledávat.  
  
-   Transformace, ověření a navigaci lze provést efektivně prostřednictvím modelu kurzoru nad daty XML, který je uložený relationally. V některých případech je možné ji provést efektivněji proti relační struktury než pokud je soubor XML uložené v **XmlDocument** modelu.  
  
-   **Datovou sadu** můžete uložit část souboru XML. To znamená, slouží **XPath** nebo **XslTransform** chcete **datovou sadu** pouze elementy a atributy, které vás zajímají. Odtud můžete změnit na menší, která jsou filtrovaná podmnožinu dat, se změnami šíření větší množství dat v **XmlDataDocument**.  
  
 Můžete také spouštět transformace dat, která byla načtena do **datovou sadu** z SQL serveru. Další možností je vytvořit vazbu formuláře Windows spravovaných styl třídy rozhraní .NET Framework a ovládacích prvků webového formuláře **datovou sadu** , který se naplní ze vstupního datového proudu XML.  
  
 Kromě podpory **XslTransform**, **XmlDataDocument** poskytuje relační data **XPath** dotazy a ověřování.  V podstatě všechny služby XML jsou k dispozici napříč relačními daty a relační zařízení, jako je například ovládací prvek vazby, codegen atd., jsou k dispozici přes strukturovaných projekce XML bez negativního vlivu věrnost XML.  
  
 Protože **XmlDataDocument** je zděděno od **třídou XMLDocument nastavenou na**, poskytuje implementaci W3C modelu DOM. Fakt, který **XmlDataDocument** je přidružený a ukládá část svých dat v rámci, **datovou sadu** omezit nebo změnit jeho použití jako **třídou XMLDocument nastavenou na** žádným způsobem. Kód napsaný využívat **třídou XMLDocument nastavenou na** funguje v nezměněném stavu proti **XmlDataDocument**. **Datovou sadu** definováním tabulky, sloupce, relace a omezení poskytuje relační zobrazení stejná data, a je úložiště dat v paměti, samostatného uživatele.  
  
 Následující obrázek znázorňuje různé přidružení, že XML data mají s **datovou sadu** a **XmlDataDocument**.  
  
 ![Datová sada XML](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 Na obrázku vidíte, že je možné načíst XML data přímo do **datovou sadu**, který umožňuje přímé manipulace s XML v relační způsobem. Nebo je možné načíst kód XML do odvozené třídy modelu DOM, který je **XmlDataDocument**a následně načtena a synchronizovat se službou **datovou sadu**. Protože **datovou sadu** a **XmlDataDocument** jsou synchronizována v rámci jedné sady dat, změny provedené v datech do jednoho úložiště se projeví v jiném úložišti.  
  
 **XmlDataDocument** dědí všechny editačních a navigačních funkce z **XmlDocument**. Existují situace, při použití **XmlDataDocument** a jeho zděděné funkcí synchronizovat se službou **datovou sadu**, je vhodnější volbou než načítání dat XML přímo do **datovésady**. V následující tabulce jsou uvedeny položky, které chcete považovat za Pokud zvolíte, jakou metodu použít k načtení **datovou sadu**.  
  
|Kdy se má načíst XML přímo do datové sady|Kdy se mají synchronizovat s datovou sadou datovým dokumentem XML|  
|----------------------------------------------|-----------------------------------------------------------|  
|Dotazy na data v **datovou sadu** jsou jednodušší díky SQL než XPath.|Dotazy XPath jsou potřeba nad daty v **datovou sadu**.|  
|Zachování řazení do zdrojového kódu XML element není důležité.|Zachování řazení do zdrojového kódu XML elementu je velmi důležité.|  
|Prázdné znaky mezi elementy a formátování nemusí být zachována v zdrojového kódu XML.|Prázdné znaky a formátování a zachovávání s rozlišením ve zdroji XML je velmi důležité.|  
  
 Pokud načtení a zápis XML přímo do a z celkového počtu **datovou sadu** řeší všechny vaše požadavky, naleznete v tématu [načtení datové sady z XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápisu datové sady jako dat XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Pokud načítání **datovou sadu** ze **XmlDataDocument** řeší všechny vaše požadavky, naleznete v tématu [synchronizace Datasetwith dokumentu XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
