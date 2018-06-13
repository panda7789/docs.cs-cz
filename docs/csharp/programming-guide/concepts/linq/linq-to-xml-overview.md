---
title: Technologie LINQ to XML přehled (C#)
ms.date: 07/20/2015
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 318c5494134fd1dd3ac2adbf538d693ad4a5dbf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339378"
---
# <a name="linq-to-xml-overview-c"></a>Technologie LINQ to XML přehled (C#)
XML byl široce přijat jako způsob formátování dat v mnoha kontexty. Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databází.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přepracovanou přístup k programování se souborem XML. Poskytuje možnosti úprav z objektu modelu dokumentu (DOM) v dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy. I když jsou tyto výrazy dotazů syntakticky liší od jazyka XPath, poskytují podobné funkce.  
  
## <a name="linq-to-xml-developers"></a>Technologie LINQ to XML vývojáři  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílem celou řadu vývojáři. Pro průměrné vývojáře, kteří právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML tím, že poskytuje podobné do SQL možnosti dotazu. S jenom kousek studii můžete postup programátory v jazyce psát dotazy stručného a výkonné v jejich programovací jazyk podle volby.  
  
 Můžete použít profesionální vývojáře [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mohou zapisovat menší kód, který je více výrazovou, kompaktnější a účinnější. Výrazy dotazů použitím z několika domén dat ve stejnou dobu.  
  
## <a name="what-is-linq-to-xml"></a>Co je technologie LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je povolené LINQ, v paměti XML programovací rozhraní, které umožňuje pracovat s XML uvnitř [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programovacích jazyků.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jako objektu modelu dokumentu (DOM) je v tom, že přináší dokumentu XML do paměti. Můžete vyhledat a upravit dokumentu, a po úpravě ho můžete uložit do souboru nebo jej serializovat a poslat přes Internet. Ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od DOM: poskytuje nový model objektu, který je světlejší váhy a snadnější pracovat, a který využívá funkce jazyka v jazyce C#.  
  
 Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Tato integrace umožňuje psát dotazy na dokument XML v paměti pro načtení kolekce elementů a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná ve funkcích (i když není v syntaxi) XPath a XQuery. Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce C# poskytuje silnější zadáte, kompilace kontrolu a vylepšenou podporu ladicí program.  
  
 Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňuje efektivní přístup pro vytváření stromů XML. Tuto metodu volá *funkční konstrukce*, umožňuje vývojářům snadno transformace stromy XML z jednoho obrazce do jiného.  
  
 Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číslo atribut pro každý element položky v nákupní objednávka:  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 Například můžete seznam seřadit podle počtu část položky s hodnotou větší než 100 USD. Chcete-li získat tyto informace, můžete spustit následující dotaz:  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:  
  
-   Načtení XML ze souborů nebo datových proudů.  
  
-   Serializace XML na soubory nebo datové proudy.  
  
-   Vytvoření XML od začátku pomocí funkční konstrukce.  
  
-   Dotaz pomocí jazyka XPath jako osy XML.  
  
-   Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Ověření XML stromy pomocí XSD.  
  
-   Použijte kombinaci těchto funkcí k transformaci stromy XML z jednoho obrazce do jiné.  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 Jednou z nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML. Například pokud chcete vytvořit malé stromu XML, můžete napsat kód následujícím způsobem:  
  
```csharp  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq>  
 [Začínáme (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
