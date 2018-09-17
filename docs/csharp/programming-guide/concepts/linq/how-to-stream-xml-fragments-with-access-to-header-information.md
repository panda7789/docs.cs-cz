---
title: 'Postupy: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 9c141b21a009f836fbf385c1f4179e288ec6c3b5
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698273"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Postupy: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)
Někdy je nutné číst libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace předvídatelné. Pokud se pokusíte k naplnění stromu XML pomocí velkého souboru XML, využití paměti bude přímo úměrná velikosti souboru – to znamená, nadměrné. Proto měli používat streamování technika místo.  
  
 Jednou z možností je pro zápis aplikace pomocí <xref:System.Xml.XmlReader>. Však můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz stromu XML. Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy. Další informace najdete v tématu [postupy: zápis metody osy XML (C#) LINQ](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Chcete-li napsat vlastní metodu osy, napište malé metody, která používá <xref:System.Xml.XmlReader> číst uzly, dokud nebude dosaženo jednoho z uzlů, které vás zajímají. Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, která čte z <xref:System.Xml.XmlReader> a vytvoří instanci XML fragment. Pak bude vrácen každý fragment prostřednictvím `yield return` v metodě, která je výčet metodu vlastní osy. Můžete pak zápis dotazů LINQ na vaše vlastní osy metoda.  
  
 Streamování techniky aplikují nejlépe v situacích, kde je potřeba zpracovat zdrojový dokument pouze jednou a může zpracovat prvky v pořadí dokumentů. Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iterovat jejich zdroj, shromáždit všechna data, seřadit a nakonec yield první položky v sekvenci. Všimněte si, že pokud použijete operátor dotazu, který bude realizována zdrojem před získávání první položka, nebude zachovat malé paměťové nároky.  
  
## <a name="example"></a>Příklad  
 Někdy problém získá jen málo další zajímavé. V následujícím dokumentu XML příjemce vaše vlastní osy metoda má také znát název zákazníka, který jednotlivé položky patří do.  
  
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
  
 Přístup, který přijímá v tomto příkladu je taky sledovat informace hlavičky, uložit informace v záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, které jsou výčet. Metoda osy poskytuje pak tento nový, malé stromu XML. Dotaz potom má přístup k informace hlavičky, jakož i podrobné informace.  
  
 Tento přístup má malé paměťové nároky. Každý detail fragment XML, je vhodné, žádné odkazy jsou omezeny na předchozí fragment, a je k dispozici pro uvolnění paměti. Všimněte si, že tento postup vytvoří mnoho krátkodobý objektů na haldě.  
  
 Následující příklad ukazuje, jak implementovat a používat vlastní osy metodu, která jsou streamována fragmentů XML ze souboru určeného identifikátorem URI. Tato vlastní osy je vytvořených speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a, tyto prvky se uspořádané jako výše `Source.xml` dokumentu. Je zjednodušenou implementaci. Robustnější implementace by být připraveni analyzovat neplatný dokument.  
  
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
  
 Tento kód vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také

- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
