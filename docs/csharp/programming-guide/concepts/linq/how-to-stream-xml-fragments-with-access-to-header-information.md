---
title: 'Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: af8f83ba746292289bb97f591103cc91d6febbad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325029"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (C#)
Někdy je nutné ke čtení libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace je předvídatelný. Pokud se pokusíte strom XML naplnění velký soubor XML, bude vaše využití paměti velikosti souboru – to znamená, nadměrné. Proto byste měli místo toho používat streamování techniku.  
  
 Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>. Ale můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování stromové struktuře XML. Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy. Další informace najdete v tématu [postupy: zápis LINQ metodě osy XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Zápis způsob osy, zápis malých metody, která používá <xref:System.Xml.XmlReader> číst uzlů, dokud nebude dosaženo jednoho z uzlů, které vás zajímá. Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, který čte z <xref:System.Xml.XmlReader> a vytvoří XML fragment. Potom dává každý fragment prostřednictvím `yield return` na metodu, která je výčet metodu vlastní osy. Poté můžete napsat dotazů LINQ na metodu vlastní osy.  
  
 Streamování techniky nejlépe použity v situacích, kdy je potřeba zpracovat zdrojový dokument jenom jednou a může zpracovat elementy v pořadí dokumentů. Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iteraci zdrojových, shromáždit všechna data, řazení ji a nakonec yield první položky v sekvenci. Všimněte si, pokud používáte operátor dotazu, který bude realizována zdrojem před je první položka, nebude zachovali malou paměťovou zátěž.  
  
## <a name="example"></a>Příklad  
 Někdy problém získá jen málo další zajímavé. V následujícím dokumentu XML má příjemce metodu vlastní osy také znát název zákazníka, které patří každou položku.  
  
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
  
 Přístup, který má v tomto příkladu je také sledovat informace hlavičky, uložit informace ze záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, která jsou vytváření výčtu. Metoda osy poskytuje pak tento nový, malé strom XML. Dotaz pak má přístup k informace hlavičky, jakož i podrobné informace.  
  
 Tento přístup má malou paměťovou zátěž. Každý fragment XML podrobností, je vhodné, jsou uchovány žádné odkazy na předchozí fragment, a je k dispozici pro uvolňování paměti. Všimněte si, že tento postup vytvoří mnoho zkrátí objektů v haldě.  
  
 Následující příklad ukazuje, jak implementovat a použít vlastní osy metodu, která datové proudy fragmenty XML ze souboru určeného identifikátor URI. Tato vlastní osy je speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a aby tyto prvky se být uspořádány jako výše `Source.xml` dokumentu. Je zneužívající vlastností prohlížeče implementace. Robustnější implementace by připravený k analýze neplatný dokument.  
  
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
 [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
