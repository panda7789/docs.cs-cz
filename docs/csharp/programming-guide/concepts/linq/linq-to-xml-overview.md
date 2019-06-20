---
title: Přehled LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 6a7d681b52bbc6ce515e2202f3f448ce4ba79ced
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267963"
---
# <a name="linq-to-xml-overview-c"></a>Přehled LINQ to XML (C#)

Technologie LINQ to XML poskytuje programovací rozhraní v paměti XML, které využívá rozhraní .NET Language-Integrated Query (LINQ). LINQ to XML použije funkce .NET a je srovnatelná se aktualizované, přepracovaný programovací rozhraní XML Document Object Model (DOM). 
 
XML je široce přijat jako způsob, jak formátování dat v mnoha kontextech. Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databázích.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přepracovaný přístup k programování v jazyce XML. Poskytuje možnosti úprav Document Object Model (DOM) dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. I když tyto výrazy dotazu představují syntakticky liší od jazyka XPath, poskytují podobné funkce.

## <a name="linq-to-xml-developers"></a>Technologie LINQ to XML vývojáře

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílí na širokou škálu vývojáři. Průměrná vývojář, který právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML pomocí prostředí dotazu, který je podobný SQL. S jen trochu studii můžete další programátorům v jejich programovací jazyk podle vlastní volby psát stručné a výkonné dotazy.

Profesionální vývojáři mohou použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit svou produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zapisují menší kód, který je více výrazovými možnostmi, kompaktnějším a výkonnější. Použitím – výrazy dotazů z několika domén dat ve stejnou dobu.

## <a name="what-is-linq-to-xml"></a>Co je LINQ to XML

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je povolené LINQ, v paměti XML programovací rozhraní, která umožňuje pracovat s jazykem XML z v rámci rozhraní .NET Framework programovacích jazyků.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je třeba Document Object Model (DOM) přináší dokumentu XML do paměti. Můžete zadávat dotazy a úpravě dokumentu a po úpravě ho můžete uložit do souboru nebo ho serializovat a odešle je prostřednictvím Internetu. Nicméně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od modelu DOM: Poskytuje nové objektový model, který je světlejší váha a snadněji pracovat, a, která využívá funkcí jazyka v C#.

Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Tato integrace umožňuje psát dotazy v dokumentu XML v paměti k načtení kolekce elementů a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelné funkci (i když nejsou v syntaxi) na XPath a XQuery. Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce C# poskytuje silnější typy, kompilace kontrolu a vylepšená podpora ladicího programu.

Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektu umožňuje efektivní přístup k vytváření stromů XML. Tomuto přístupu se říká *funkční konstrukce*, umožňuje vývojářům snadno transformace stromů XML z jednoho obrazce na jiný.

Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). S použitím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číselné atribut pro každý prvek položky v nákupní objednávky:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

To může být přepsán ve formuláři syntaxe metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Další příklad můžete seznam seřazený podle čísel položky s hodnotou větší než 100 USD. Pro získání těchto informací, můžete spustit následující dotaz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Znovu to může být přepsán ve formuláři syntaxe metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:

- Načtení XML ze [soubory](how-to-load-xml-from-a-file.md) nebo [datové proudy](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializace XML pro soubory nebo datové proudy.

- Vytvoření XML od začátku pomocí funkční konstrukce.

- Dotaz XML pomocí XPath jako osy.

- Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Ověření pomocí XSD stromů XML.

- Pomocí kombinace těchto funkcí transformace stromů XML z jednoho obrazce do jiné.

## <a name="creating-xml-trees"></a>Vytváření stromů XML

Jednou z nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytváření stromů XML. Například k vytvoření malé stromu XML, můžete napsat kód následujícím způsobem:

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

Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Viz také:

- [Referenční informace (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [Technologie LINQ to XML versus DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [Technologie LINQ to XML versus jiné technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
