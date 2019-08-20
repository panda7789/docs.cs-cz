---
title: 'Postupy: Streamování fragmentů XML z objektuC#XmlReader ()'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: c27c2165af95b8b781564e14efc0668f596e3057
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592405"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Postupy: Streamování fragmentů XML z objektuC#XmlReader ()
V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak streamovat fragmenty <xref:System.Xml.XmlReader>pomocí.  
  
 Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení <xref:System.Xml.Linq.XElement> objektů, je napsat vlastní metodu vlastní osy. Metoda Axis obvykle vrací kolekci <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jako je například, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy po vytvoření fragmentu XML voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody vraťte kolekci pomocí. `yield return` To poskytuje sémantiku pro odložené provádění vlastní metody osy.  
  
 Při vytváření stromu XML z <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader> musí být umístěn na elementu. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda se nevrátí, dokud nepřečetla uzavírací značku elementu.  
  
 Chcete-li vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>objektu, umístit čtenáře na uzel, který chcete převést <xref:System.Xml.Linq.XElement> na strom <xref:System.Xml.Linq.XElement> , a poté vytvořit objekt.  
  
 Téma [postupy: Streamování fragmentů XML s přístupem k informacímC#hlavičky](./how-to-stream-xml-fragments-with-access-to-header-information.md) () obsahuje informace a příklad, jak streamovat složitější dokument.  
  
 Téma [postupy: Transformace streamování velkých dokumentů XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní metodu osy. Dotaz můžete vytvořit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocí dotazu. Vlastní metoda osy, `StreamRootChildDoc`, je metoda, která je navržena speciálně pro čtení dokumentu, který má opakující `Child` se element.  
  
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
  
```  
bbb  
ccc  
```  
  
 V tomto příkladu je zdrojový dokument velmi malý. Nicméně i v případě, že existovaly `Child` miliony prvků, by tento příklad měl stále malou zátěž paměti.  
  