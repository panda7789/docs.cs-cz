---
title: LinQ na XML Přehled (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168412"
---
# <a name="linq-to-xml-overview-c"></a>LinQ na XML Přehled (C#)

LINQ na XML poskytuje programovací rozhraní XML v paměti, které využívá rozhraní LINQ (Language-Integrated Query) .NET.NET to XML provides a in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework. LINQ to XML používá možnosti rozhraní .NET a je srovnatelný s aktualizovaným přepracovaným programovacím rozhraním XML objektového modelu dokumentu (DOM).

Jazyk XML byl široce přijat jako způsob formátování dat v mnoha kontextech. Xml můžete například najít na webu, v konfiguračních souborech, v souborech aplikace Microsoft Office Word a v databázích.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je aktuální, přepracovaný přístup k programování pomocí XML. Poskytuje možnosti úpravy dokumentu v paměti modelu DOCUMENT Object Model (DOM) a podporuje výrazy dotazu LINQ. Přestože tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.

## <a name="linq-to-xml-developers"></a>LINQ vývojářům XML

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zaměřuje na různé vývojáře. Pro průměrného vývojáře, který chce [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jen něco udělat, usnadňuje XML tím, že poskytuje prostředí dotazu, které je podobné SQL. S trochou studia se programátoři mohou naučit psát stručné a výkonné dotazy ve svém programovacím jazyce.

Profesionální vývojáři [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] mohou využít k výraznému zvýšení jejich produktivity. S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mohou psát méně kódu, který je výraznější, kompaktnější a výkonnější. Mohou používat výrazy dotazu z více datových domén současně.

## <a name="what-is-linq-to-xml"></a>Co je LINQ na XML?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je programovací rozhraní XML s podporou linq v paměti, které umožňuje pracovat s jazykem XML z programovacích jazyků rozhraní .NET Framework.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je jako document object model (DOM) v tom, že přináší dokument XML do paměti. Dokument můžete dotazovat a upravovat a po jeho úpravě jej můžete uložit do souboru nebo jej serializovat a odeslat přes Internet. Liší [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se však od modelu DOM: Poskytuje nový objektový model, který je lehčí a snadněji se s ním pracuje a který využívá funkce jazyka v jazyce C#.

Nejdůležitější výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je jeho integrace s jazykem integrovaný dotaz (LINQ). Tato integrace umožňuje psát dotazy na dokument XML v paměti k načtení kolekcí prvků a atributů. Možnost dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná ve funkčnosti (i když ne v syntaxi) s XPath a XQuery. Integrace LINQ v C# poskytuje silnější psaní, kontrolu v době kompilace a vylepšenou podporu ladicího programu.

Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použít výsledky dotazu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> jako parametry a konstruktory objektů umožňuje výkonný přístup k vytváření stromů XML. Tento přístup, nazývaný *funkční konstrukce*, umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce do druhého.

Můžete mít například typickou nákupní objednávku XML popsanou v [ukázkovém souboru XML: Typická nákupní objednávka (LINQ to XML).](sample-xml-file-typical-purchase-order-linq-to-xml-1.md) Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete spustit následující dotaz a získat hodnotu atributu číslo dílu pro každý prvek položky v nákupní objednávce:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

To lze přepsat ve formě syntaxe metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Jako další příklad můžete chtít seznam položek s hodnotou větší než 100 Kč seřazený podle čísla dílu. Chcete-li získat tyto informace, můžete spustit následující dotaz:

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

Opět platí, že to to může být přepsána ve formě syntaxe metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Kromě těchto funkcí LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML. Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete:

- Načtěte XML ze [souborů](how-to-load-xml-from-a-file.md) nebo [datových proudů](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serialize XML na soubory nebo datové proudy.

- Vytvořte XML od začátku pomocí funkční konstrukce.

- Dotaz XML pomocí xpath-jako osy.

- Manipulujte se stromem XML v paměti <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A>pomocí <xref:System.Xml.Linq.XNode.ReplaceWith%2A>metod, jako jsou například , , a <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Ověřte stromy XML pomocí xsd.

- Pomocí kombinace těchto funkcí můžete transformovat stromy XML z jednoho obrazce do druhého.

## <a name="creating-xml-trees"></a>Vytváření stromů XML

Jednou z nejvýznamnějších výhod programování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s je, že je snadné vytvářet xml stromy. Chcete-li například vytvořit malý strom XML, můžete napsat kód následujícím způsobem:

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

Další informace naleznete [v tématu Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Viz také

- [Referenční informace (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ na XML vs. DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ na XML vs. jiné technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
