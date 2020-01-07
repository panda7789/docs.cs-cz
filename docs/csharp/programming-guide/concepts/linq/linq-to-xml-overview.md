---
title: Přehled LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: d8b606e1d3287f13a2112b75d5239fd1ac7dd7dc
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635506"
---
# <a name="linq-to-xml-overview-c"></a>Přehled LINQ to XML (C#)

LINQ to XML poskytuje rozhraní pro programování XML v paměti, které využívá architekturu LINQ (Integrated Query) jazyka .NET. LINQ to XML využívá možnosti rozhraní .NET a je porovnatelný z aktualizovaného a přepracovaného programovacího rozhraní XML model DOM (Document Object Model) (DOM). 
 
Soubor XML byl široce přijat jako způsob, jak formátovat data v mnoha kontextech. Můžete například najít XML na webu, v konfiguračních souborech, v systém Microsoft Office soubory aplikace Word a v databázích.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je aktuální, přenavržený přístup k programování s XML. Poskytuje funkce pro úpravy dokumentů v paměti model DOM (Document Object Model) (DOM) a podporuje výrazy dotazů LINQ. I když tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.

## <a name="linq-to-xml-developers"></a>LINQ to XML vývojáři

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] cílí na celou řadu vývojářů. Pro průměrného vývojáře, který chce jenom udělat, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje práci s XML pomocí dotazů, které jsou podobné SQL. S pouhou bitovou studiem se programátoři můžou naučit psát stručné a výkonné dotazy v programovacím jazyce, který si vyberete.

Profesionální vývojáři můžou pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] významně zvýšit produktivitu. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžou napsat méně kódu, který je více expresější, kompaktnější a výkonnější. Můžou používat výrazy dotazů z více domén dat současně.

## <a name="what-is-linq-to-xml"></a>Co je LINQ to XML?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je programovací rozhraní XML v paměti, které umožňuje pracovat s XML v rámci .NET Framework programovacích jazyků.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je stejně jako model DOM (Document Object Model) (DOM) v tom, že převede dokument XML do paměti. Můžete provést dotazování a úpravy dokumentu a až ho upravíte, můžete ho uložit do souboru nebo ho serializovat a poslat přes Internet. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se však liší od modelu DOM: poskytuje nový objektový model, který je světlejší o váhu a usnadňuje práci s a který využívá funkce jazyka v C#.

Nejdůležitější výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je jeho integrace s LINQ (Language-Integrated Query). Tato integrace umožňuje zapisovat dotazy v dokumentu XML v paměti pro načtení kolekcí prvků a atributů. Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná s funkcemi (i když není v syntaxi) do XPath a XQuery. Integrace LINQ v C# systému poskytuje silnější psaní, kontrolu doby kompilace a vylepšenou podporu ladicího programu.

Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použití výsledků dotazu jako parametrů pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektů umožňuje účinný přístup k vytváření stromů XML. Tento přístup s názvem *funkční konstrukce*umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce na druhý.

Například můžete mít typické nákupní objednávky XML, jak je popsáno v [ukázkovém souboru XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete spustit následující dotaz pro získání hodnoty atributu číslo součásti pro každý prvek položky v nákupní objednávce:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Toto lze přepsat ve formě syntaxe metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Jako další příklad můžete chtít seznam, který je seřazen podle čísla součásti, u položek s hodnotou větší než $100. Chcete-li získat tyto informace, můžete spustit následující dotaz:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Tuto akci lze znovu zapsat ve formě syntaxe metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Kromě těchto možností LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete:

- Načte XML ze [souborů](how-to-load-xml-from-a-file.md) nebo [datových proudů](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializace XML do souborů nebo datových proudů.

- Vytvořte XML od začátku pomocí funkční konstrukce.

- Dotazování XML pomocí osy jako XPath

- Manipulace se stromovou strukturou XML v paměti pomocí metod, jako je <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>a <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Ověří stromy XML pomocí XSD.

- Použijte kombinaci těchto funkcí pro transformaci stromů XML z jednoho obrazce do jiného.

## <a name="creating-xml-trees"></a>Vytváření stromů XML

Jednou z nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je snadné vytváření stromů XML. Například pro vytvoření malého stromu XML můžete napsat kód následujícím způsobem:

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

Další informace naleznete v tématu [CREATING XML TreesC#()](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Viz také:

- [Referenční informace (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ to XML vs. DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ to XML vs. další technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
