---
title: Postup streamování fragmentů XML z objektu XmlReaderC#()
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 20fa4096a79648edc3f5d699f764fc6d71fa0ba4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635649"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Postup streamování fragmentů XML z objektu XmlReaderC#()
V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader>.  
  
 Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení objektů <xref:System.Xml.Linq.XElement>, je napsat vlastní metodu vlastní osy. Metoda Axis obvykle vrací kolekci, například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy po vytvoření fragmentu XML voláním metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> vraťte kolekci pomocí `yield return`. To poskytuje sémantiku pro odložené provádění vlastní metody osy.  
  
 Při vytváření stromu XML z objektu <xref:System.Xml.XmlReader> musí být <xref:System.Xml.XmlReader> umístěn na elementu. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nevrátí, dokud nepřečetla uzavírací značku elementu.  
  
 Chcete-li vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístit čtecí modul na uzel, který chcete převést na <xref:System.Xml.Linq.XElement> stromu, a poté vytvořit objekt <xref:System.Xml.Linq.XElement>.  
  
Téma, [jak streamovat fragmenty XML s přístupem k informacím hlavičkyC#()](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.
  
 Téma, [Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování](./how-to-perform-streaming-transform-of-large-xml-documents.md) , obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní metodu osy. Můžete se k němu dotázat pomocí dotazu LINQ. Vlastní metoda osy, `StreamRootChildDoc`, je metoda, která je určena specificky pro čtení dokumentu, který má opakující se `Child` element.  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
bbb  
ccc  
```  
  
 V tomto příkladu je zdrojový dokument velmi malý. Nicméně i v případě, že existovaly miliony `Child` prvků, bude mít tento příklad pořád malou paměť.  
  