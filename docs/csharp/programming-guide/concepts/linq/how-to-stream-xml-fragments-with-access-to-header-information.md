---
title: Postup při streamování fragmentů XML s přístupem k informacímC#hlavičky ()
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712387"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Postup při streamování fragmentů XML s přístupem k informacímC#hlavičky ()
Někdy je nutné číst libovolně velké soubory XML a napsat aplikaci tak, aby paměti aplikace byly předvídatelné. Pokud se pokusíte naplnit strom XML velkým souborem XML, využití paměti bude úměrné velikosti souboru, tedy nadměrné. Proto byste měli místo toho použít metodu streamování.  
  
Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>. Můžete však chtít použít LINQ k dotazování stromu XML. Pokud se jedná o tento případ, můžete napsat vlastní metodu osy. Další informace najdete v tématu [Postup zápisu metody osy LINQ to XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).
  
 Chcete-li napsat vlastní metodu osy, napíšete malou metodu, která používá <xref:System.Xml.XmlReader> ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají. Metoda pak zavolá <xref:System.Xml.Linq.XNode.ReadFrom%2A>, které čtou z <xref:System.Xml.XmlReader> a vytvoří instanci fragmentu XML. Následně výsledkem každého fragmentu `yield return` metoda, která vytváří výčet vlastní metody osy. Pak můžete napsat dotazy LINQ na vlastní metodu osy.  
  
 Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů. Některé standardní operátory pro dotazování, jako je například <xref:System.Linq.Enumerable.OrderBy%2A>, iterují jejich zdroj, shromažďují všechna data, řadí je a nakonec vydávají první položku v sekvenci. Pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si uchovávat malý objem paměti.  
  
## <a name="example"></a>Příklad  

Někdy je problém jenom trochu zajímavější. V následujícím dokumentu XML musí příjemce vlastní metody osy také znát název zákazníka, ke kterému každá položka patří.  
  
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
  
 Přístup v tomto příkladu je také sledován pro tyto informace hlavičky, uložení informací v hlavičce a následné sestavení malého stromu XML, který obsahuje jak informace v hlavičce, tak i podrobnosti, které provádíte ve výčtu. Metoda Axis pak tento nový malý strom XML. Dotaz pak má přístup k informacím v hlavičce a také k podrobným informacím.  
  
 Tento přístup má malé nároky na paměť. Vzhledem k tomu, že se přestanou fragmenty XML, nezachovají se žádné odkazy na předchozí fragment a je k dispozici pro uvolňování paměti. Tato technika vytvoří mnoho krátkodobých objektů v haldě.  
  
 Následující příklad ukazuje, jak implementovat a použít vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI. Tato vlastní osa je zapsána tak, že očekává dokument, který má `Customer`, `Name`a `Item` prvky a že tyto prvky budou uspořádány jako v předchozím `Source.xml` dokumentu. Jedná se o zjednodušený implementaci. Robustnější implementace by se připravila k analýze neplatného dokumentu.  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Root>  
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
</Root>  
```  
