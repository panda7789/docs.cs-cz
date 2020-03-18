---
title: Jak provést streamování transformace velkých dokumentů XML (C#)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 9eb2e832f798e550ef3b534b0c9a0e3416378b43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169101"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Jak provést streamování transformace velkých dokumentů XML (C#)
Někdy budete muset transformovat velké soubory XML a zapsat aplikaci tak, aby nároky na paměť aplikace je předvídatelné. Pokud se pokusíte naplnit strom XML velmi velkým souborem XML, bude využití paměti úměrné velikosti souboru (to znamená nadměrné). Proto byste měli místo toho použít techniku streamování.  
  
 Techniky streamování jsou nejvhodnější v situacích, kdy je třeba zpracovat zdrojový dokument pouze jednou a prvky můžete zpracovat v pořadí dokumentů. Některé standardní operátory <xref:System.Linq.Enumerable.OrderBy%2A>dotazů, například , iterate jejich zdroj, shromažďovat všechna data, seřadit a nakonec výnos první položku v pořadí. Všimněte si, že pokud použijete operátor dotazu, který zhmotní jeho zdroj před získávání první položky, nezachováte malé nároky na paměť pro vaši aplikaci.  
  
I v případě, že použijete techniku popsanou v [jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#),](./how-to-stream-xml-fragments-with-access-to-header-information.md)pokud se pokusíte sestavit strom XML, který obsahuje transformovaný dokument, využití paměti bude příliš velké.
  
 Existují dva hlavní přístupy. Jedním z přístupů je použití <xref:System.Xml.Linq.XStreamingElement>odložených vlastností zpracování . Dalším přístupem je <xref:System.Xml.XmlWriter>vytvoření a použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] možností zápisu <xref:System.Xml.XmlWriter>prvků do rozhraní . Toto téma ukazuje oba přístupy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vychází z příkladu v [části Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#).](./how-to-stream-xml-fragments-with-access-to-header-information.md)
  
 Tento příklad používá možnosti <xref:System.Xml.Linq.XStreamingElement> odložené spuštění k streamování výstupu. Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.  
  
 Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml. Robustnější implementace by však byla připravena analyzovat neplatný dokument.  
  
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
Následující příklad také vychází z příkladu v [části Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#).](./how-to-stream-xml-fragments-with-access-to-header-information.md)
  
 Tento příklad používá [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] schopnost psát prvky do . <xref:System.Xml.XmlWriter> Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.  
  
 Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml. Robustnější implementace by však buď ověřit zdrojový dokument s XSD, nebo by byla připravena analyzovat neplatný dokument.  
  
 Tento příklad používá stejný zdrojový dokument Source.xml jako předchozí příklad v tomto tématu. Také produkuje přesně stejný výstup.  
  
 Použití <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupního XML je <xref:System.Xml.XmlWriter>upřednostňováno před zápisem do .  
  
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
  