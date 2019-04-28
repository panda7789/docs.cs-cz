---
title: 'Postupy: Provedení streamované transformace velkých dokumentů XML (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 8ddd7e25cf160526b741db5769a78682970c3724
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701954"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Postupy: Provedení streamované transformace velkých dokumentů XML (C#)
Někdy je nutné transformovat velké soubory XML a zápis aplikace tak, aby nároky na paměť pro aplikace předvídatelné. Pokud se pokusíte naplnění stromu XML pomocí velmi velkých souborů XML, využití paměti bude přímo úměrná velikosti souboru (to znamená, nadměrné). Proto měli používat streamování technika místo.  
  
 Streamování techniky aplikují nejlépe v situacích, kde je potřeba zpracovat zdrojový dokument pouze jednou a může zpracovat prvky v pořadí dokumentů. Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iterovat jejich zdroj, shromáždit všechna data, seřadit a nakonec yield první položky v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který bude realizována zdrojem před získávání první položka, nebudou zachovány malé paměťové nároky pro vaši aplikaci.  
  
 I když používáte podle postupu popsaného v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit stromu XML obsahující transformovaná dokument, bude příliš velké využití paměti.  
  
 Existují dva hlavní přístupy. Jedním z přístupů je použít vlastnosti odložené zpracování <xref:System.Xml.Linq.XStreamingElement>. Další možností je vytvořit <xref:System.Xml.XmlWriter>a s využitím možností [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapisovat elementy, které chcete <xref:System.Xml.XmlWriter>. Toto téma ukazuje oba přístupy.  
  
## <a name="example"></a>Příklad  
 Následující příklad je založen na příklad v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Tento příklad používá možnosti odložené provedení <xref:System.Xml.Linq.XStreamingElement> Streamovat výstup. V tomto příkladu můžete transformovat velmi velkých dokumentů při zachování malé paměťové nároky.  
  
 Všimněte si, že vlastní osy (`StreamCustomerItem`) je konkrétně napsána tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` prvky. proto, že tyto prvky se uspořádané jako v následujícím dokumentu Source.xml. Robustnější implementace by však připravit analyzovat neplatný dokument.  
  
 Následuje zdrojovém dokumentu Source.xml:  
  
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
  
 Tento kód vytvoří následující výstup:  
  
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
 Následující příklad také vytvoří v příkladu v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 Tento příklad používá funkci aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapisovat elementy, které chcete <xref:System.Xml.XmlWriter>. V tomto příkladu můžete transformovat velmi velkých dokumentů při zachování malé paměťové nároky.  
  
 Všimněte si, že vlastní osy (`StreamCustomerItem`) je konkrétně napsána tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` prvky. proto, že tyto prvky se uspořádané jako v následujícím dokumentu Source.xml. Robustnější implementaci, ale by buď ověřit zdrojový dokument s XSD nebo bude připravený k analýze neplatný dokument.  
  
 Tento příklad používá stejný zdrojový dokument Source.xml, stejně jako v předchozím příkladu v tomto tématu. Vytvoří také přesně stejný výstup.  
  
 Pomocí <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupním souboru XML je upřednostňované nad zápisu do <xref:System.Xml.XmlWriter>.  
  
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
  
 Tento kód vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
