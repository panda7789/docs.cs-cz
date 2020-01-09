---
title: Integrace XML s relačními daty a ADO.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
ms.openlocfilehash: 373e28d1fffd8c47acb4acb70271db056aa3a27b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709930"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>Integrace XML s relačními daty a ADO.NET
Třída **objektu XmlDataDocument** je odvozenou třídou **XmlDocument**a obsahuje data XML. Výhodou **objektu XmlDataDocument** je, že poskytuje most mezi relačními a hierarchickými daty. Je to **XmlDocument** , který může být svázán s **datovou sadou** a obě třídy mohou synchronizovat změny provedené v datech, která jsou obsažena v obou třídách. Element **XmlDocument** , který je svázán s **datovou sadou** , umožňuje integraci XML s relačními daty a vy nemusíte mít data reprezentovaná buď jako XML, nebo v relačním formátu. Můžete to provést i bez omezení na jednu reprezentaci dat.  
  
 Výhody, které mají data k dispozici ve dvou zobrazeních:  
  
- Strukturovaná část dokumentu XML může být mapována na datovou sadu a efektivně uložená, indexovaná a prohledávaná.  
  
- Transformace, ověřování a navigace lze provádět efektivně prostřednictvím modelu kurzoru nad daty XML, která jsou uložena ve vztahu. V některých případech je možné to efektivněji udělat proti relačním strukturám, než když je XML uložený v modelu **XmlDocument** .  
  
- **Datová sada** může obsahovat část XML. To znamená, že můžete použít **XPath** nebo **XslTransform** k ukládání do **datové sady** , které obsahují pouze prvky a atributy, které mají zájem. Odtud můžete provádět změny menší, filtrované podmnožiny dat a změny, které se šíří na větší data v **objektu XmlDataDocument**.  
  
 Můžete také spustit transformaci dat, která byla načtena do **datové sady** z SQL Server. Další možností je vytvořit vazby .NET Framework spravovaných třídami – DataGridView a ovládací prvky WebForm na **datovou sadu** , která byla naplněna ze vstupního datového proudu XML.  
  
 Kromě podpory **XslTransform**poskytuje **objektu XmlDataDocument** relační data pro dotazy a ověřování **XPath** .  V podstatě jsou k dispozici všechny služby XML přes relační data a relační zařízení, jako jsou vazby ovládacího prvku, CODEGEN a tak dále, jsou k dispozici prostřednictvím strukturované projekce XML bez narušení přesnosti XML.  
  
 Vzhledem k tomu, že **objektu XmlDataDocument** je zděděn z prvku **XmlDocument**, poskytuje implementaci konsorcia W3C DOM. Skutečnost, že **objektu XmlDataDocument** je přidružen k a ukládá podmnožinu svých dat v rámci, **datová sada** neomezuje ani nemění použití jako **XmlDocument** jakýmkoli způsobem. Kód napsaný pro využívání prvku **XmlDocument** funguje nezměněný na **objektu XmlDataDocument**. **Datová sada** poskytuje relační pohled na stejná data definováním tabulek, sloupců, vztahů a omezení a jedná se o samostatné úložiště uživatelských dat v paměti.  
  
 Následující ilustrace znázorňuje různá přidružení, která obsahují data XML s **datovou sadou** a **objektu XmlDataDocument**: 
  
 ![Diagram, který zobrazuje různá přidružení s datovou sadou XML.](./media/xml-integration-with-relational-data-and-adonet/xml-integration-relational-data-adodotnet.gif)  
  
 Ilustrace ukazuje, že data XML lze načíst přímo do **datové sady**, která umožňuje přímou manipulaci s XML relačním způsobem. Nebo lze XML načíst do odvozené třídy modelu DOM, která je **objektu XmlDataDocument**a následně načtena a synchronizována s **datovou sadou**. Vzhledem k tomu, že **datová sada** a **objektu XmlDataDocument** se synchronizují přes jednu sadu dat, změny provedené v datech v jednom úložišti se projeví i v jiném úložišti.  
  
 **Objektu XmlDataDocument** zdědí všechny editační a navigační funkce z **XmlDocument**. Existují situace, kdy použití **objektu XmlDataDocument** a zděděných funkcí synchronizované s **datovou sadou**je VHODNĚJŠÍ možnost než načtení XML přímo do **datové sady**. Následující tabulka obsahuje položky, které je třeba vzít v úvahu při výběru metody, která se má použít pro načtení **datové sady**.  
  
|Kdy načíst XML přímo do datové sady|Kdy synchronizovat objektu XmlDataDocument s datovou sadou|  
|----------------------------------------------|-----------------------------------------------------------|  
|Dotazy na data v **datové sadě** usnadňují používání jazyka SQL než XPath.|Dotazy XPath jsou požadovány pro data v **datové sadě**.|  
|Zachování řazení elementů ve zdrojovém kódu XML není kritické.|Zachování řazení elementů ve zdrojovém kódu XML je kritické.|  
|Prázdné znaky mezi elementy a formátování není nutné uchovávat ve zdrojovém kódu XML.|Zachování prázdného místa a formátování ve zdrojovém kódu XML je kritické.|  
  
 Pokud se načítají a zapisují XML přímo do nebo z **datové sady** , které vaše potřeby řeší, přečtěte si téma [načtení datové sady z XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápis datové sady jako XML data](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Pokud načítáte **datovou sadu** z **objektu XmlDataDocument** adres, přečtěte si článek [synchronizace datové sady s dokumentem XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
