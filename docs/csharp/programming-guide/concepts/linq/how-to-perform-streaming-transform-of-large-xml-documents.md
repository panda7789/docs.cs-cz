---
title: Jak provést transformaci velkých dokumentů XML pomocí streamování (C#)
description: Naučte se, jak provést transformaci textu do XML v jazyce C# a vyhnout se nadměrnému využití paměti u některých souborů.
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: e1ab2866079b2244dc764271d7ba63173349e2f3
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104867"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Jak provést transformaci velkých dokumentů XML pomocí streamování (C#)
Někdy je nutné transformovat velké soubory XML a napsat aplikaci tak, aby paměťové nároky aplikace byly předvídatelné. Pokud se pokusíte naplnit strom XML s velmi velkým souborem XML, využití paměti bude úměrné velikosti souboru (to znamená nadměrné). Proto byste měli místo toho použít metodu streamování.  
  
 Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů. Některé standardní operátory pro dotazování, jako <xref:System.Linq.Enumerable.OrderBy%2A> je například iterace zdroje, shromáždění všech dat, jejich řazení a nakonec vydávají první položku v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si u své aplikace uchovávat malý objem paměti.  
  
I v případě, že použijete techniku popsanou v tématu [postup streamování fragmentů XML s přístupem k informacím hlavičky (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit strom XML obsahující transformovaný dokument, využití paměti bude příliš Skvělé.
  
 Existují dva hlavní přístupy. Jedním z možností je použít odložené charakteristiky zpracování <xref:System.Xml.Linq.XStreamingElement> . Dalším přístupem je vytvoření <xref:System.Xml.XmlWriter> a použití možností [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro zápis prvků do <xref:System.Xml.XmlWriter> . Toto téma ukazuje oba přístupy.  
  
## <a name="example"></a>Příklad  
 Následující příklad je sestaven na příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacím hlavičky (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 V tomto příkladu se používá odložené možnosti spuštění <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupu. Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.  
  
 Všimněte si, že vlastní osa ( `StreamCustomerItem` ) je specificky napsána tak, že očekává dokument, který obsahuje `Customer` `Name` prvky, a a `Item` že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml. Robustnější implementace by ale mohla být připravená analyzovat neplatný dokument.  
  
 Následuje zdrojový dokument Source.xml:  
  
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
Následující příklad také sestavení je v příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacím hlavičky (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 Tento příklad používá schopnost [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro zápis prvků do <xref:System.Xml.XmlWriter> . Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.  
  
 Všimněte si, že vlastní osa ( `StreamCustomerItem` ) je specificky napsána tak, že očekává dokument, který obsahuje `Customer` `Name` prvky, a a `Item` že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml. Robustnější implementace však buď ověří zdrojový dokument s XSD, nebo by bylo připraveno analyzovat neplatný dokument.  
  
 Tento příklad používá stejný zdrojový dokument, Source.xml, jako předchozí příklad v tomto tématu. Vytvoří také přesně stejný výstup.  
  
 <xref:System.Xml.Linq.XStreamingElement>Při použití pro streamování je výstup XML preferovaný před zápisem do <xref:System.Xml.XmlWriter> .  
  
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
  