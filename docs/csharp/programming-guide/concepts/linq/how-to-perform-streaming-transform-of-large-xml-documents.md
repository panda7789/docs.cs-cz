---
title: Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 86b74534635dcca7e8c7f94873abcb50ea7c4d2b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345816"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování
Někdy je nutné transformovat velké soubory XML a napsat aplikaci tak, aby paměťové nároky aplikace byly předvídatelné. Pokud se pokusíte naplnit strom XML s velmi velkým souborem XML, využití paměti bude úměrné velikosti souboru (to znamená nadměrné). Proto byste měli místo toho použít metodu streamování.  
  
 Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů. Některé standardní operátory pro dotazování, jako je například <xref:System.Linq.Enumerable.OrderBy%2A>, iterují jejich zdroj, shromažďují všechna data, řadí je a nakonec vydávají první položku v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si u své aplikace uchovávat malý objem paměti.  
  
I v případě, že použijete techniku popsanou v tématu [postup streamování fragmentů XML sC#přístupem k informacím hlavičky ()](./how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit strom XML obsahující transformovaný dokument, využití paměti bude příliš Skvělé.
  
 Existují dva hlavní přístupy. Jednou z možností je použít odložené zpracování vlastností <xref:System.Xml.Linq.XStreamingElement>. Dalším přístupem je vytvoření <xref:System.Xml.XmlWriter>a použití možností [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k zápisu prvků do <xref:System.Xml.XmlWriter>. Toto téma ukazuje oba přístupy.  
  
## <a name="example"></a>Příklad  
 Následující příklad je sestaven na příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacím hlavičkyC#()](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 V tomto příkladu se k streamování výstupu používá funkce odloženého spuštění <xref:System.Xml.Linq.XStreamingElement>. Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.  
  
 Všimněte si, že vlastní osa (`StreamCustomerItem`) je specificky zapsána, takže očekává dokument, který obsahuje prvky `Customer`, `Name`a `Item` a že tyto prvky budou uspořádány jako v následujícím dokumentu source. XML. Robustnější implementace by ale mohla být připravená analyzovat neplatný dokument.  
  
 Následuje zdrojový dokument source. XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
Následující příklad také sestaví na příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacímC#hlavičky ()](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 Tento příklad používá schopnost [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k zápisu prvků do <xref:System.Xml.XmlWriter>. Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.  
  
 Všimněte si, že vlastní osa (`StreamCustomerItem`) je specificky zapsána, takže očekává dokument, který obsahuje prvky `Customer`, `Name`a `Item` a že tyto prvky budou uspořádány jako v následujícím dokumentu source. XML. Robustnější implementace však buď ověří zdrojový dokument s XSD, nebo by bylo připraveno analyzovat neplatný dokument.  
  
 Tento příklad používá stejný zdrojový dokument, source. XML, jako předchozí příklad v tomto tématu. Vytvoří také přesně stejný výstup.  
  
 Při použití <xref:System.Xml.Linq.XStreamingElement> pro streamování je výstupní soubor XML preferovaný před zápisem do <xref:System.Xml.XmlWriter>.  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  