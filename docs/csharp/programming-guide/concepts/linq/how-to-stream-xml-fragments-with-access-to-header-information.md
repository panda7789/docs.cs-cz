---
title: Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712387"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)
Někdy budete muset číst libovolně velké soubory XML a zapsat aplikaci tak, aby nároky na paměť aplikace je předvídatelné. Pokud se pokusíte naplnit strom XML velkým souborem XML, bude využití paměti úměrné velikosti souboru , tj. Proto byste měli místo toho použít techniku streamování.  
  
Jednou z možností je <xref:System.Xml.XmlReader>napsat aplikaci pomocí aplikace . Můžete však chtít použít LINQ k dotazování stromu XML. Pokud se jedná o tento případ, můžete napsat vlastní metodu vlastní osy. Další informace naleznete [v tématu Jak napsat metodu osy LINQ do XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).
  
 Chcete-li napsat vlastní metodu osy, <xref:System.Xml.XmlReader> napište malou metodu, která používá ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají. Metoda pak <xref:System.Xml.Linq.XNode.ReadFrom%2A>volá , který <xref:System.Xml.XmlReader> čte z a konkretizovat xml fragment. Potom výnosy každý `yield return` fragment až do metody, která je výčet vlastní metody osy. Potom můžete psát dotazy LINQ na vlastní metodu osy.  
  
 Techniky streamování jsou nejvhodnější v situacích, kdy je třeba zpracovat zdrojový dokument pouze jednou a prvky můžete zpracovat v pořadí dokumentů. Některé standardní operátory <xref:System.Linq.Enumerable.OrderBy%2A>dotazů, například , iterate jejich zdroj, shromažďovat všechna data, seřadit a nakonec výnos první položku v pořadí. Pokud použijete operátor dotazu, který zhmotní jeho zdroj před výnosem první položky, nezachováte malé nároky na paměť.  
  
## <a name="example"></a>Příklad  

Někdy je problém trochu zajímavější. V následujícím dokumentu XML musí příjemce metody vlastní osy také znát jméno zákazníka, ke kterému každá položka patří.  
  
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
  
 Přístup, který tento příklad používá, je také sledovat informace o tomto záhlaví, uložit informace záhlaví a potom vytvořit malý strom XML, který obsahuje informace záhlaví a podrobnosti, které jsou výčet. Metoda osy pak dává tento nový, malý strom XML. Dotaz pak má přístup k informacím záhlaví, stejně jako podrobné informace.  
  
 Tento přístup má malé nároky na paměť. Jako každý detail XML fragment je výnosný, žádné odkazy jsou uchovávány na předchozí fragment a je k dispozici pro uvolňování paměti. Tato technika vytvoří mnoho objektů s krátkou životností na haldě.  
  
 Následující příklad ukazuje, jak implementovat a používat vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI. Tato vlastní osa je napsána tak, `Name`že `Item` očekává dokument, který má `Customer`, , `Source.xml` a prvky a že tyto prvky budou uspořádány jako ve výše uvedeném dokumentu. Jedná se o zjednodušující implementaci. Robustnější implementace by byla připravena k analýzě neplatného dokumentu.  
  
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
