---
title: Postup streamování fragmentů XML ze třídy XmlReader (C#)
description: Naučte se streamovat fragmenty XML z objektu XmlReader. Tato metoda se používá pro zpracování velkých souborů XML.
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301018"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Postup streamování fragmentů XML ze třídy XmlReader (C#)

V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader> .  
  
 Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení <xref:System.Xml.Linq.XElement> objektů, je napsat vlastní metodu vlastní osy. Metoda Axis obvykle vrací kolekci, jako je například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy po vytvoření fragmentu XML voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody vraťte kolekci pomocí `yield return` . To poskytuje sémantiku pro odložené provádění vlastní metody osy.  
  
 Při vytváření stromu XML z <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader> musí být umístěn na elementu. <xref:System.Xml.Linq.XNode.ReadFrom%2A>Metoda se nevrátí, dokud nepřečetla uzavírací značku elementu.  
  
 Chcete-li vytvořit částečný strom, můžete vytvořit instanci objektu <xref:System.Xml.XmlReader> , umístit čtenáře na uzel, který chcete převést na <xref:System.Xml.Linq.XElement> strom, a poté vytvořit <xref:System.Xml.Linq.XElement> objekt.  
  
Téma, [jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.
  
 Téma, [Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování](./how-to-perform-streaming-transform-of-large-xml-documents.md) , obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní metodu osy. Můžete se k němu dotázat pomocí dotazu LINQ. Vlastní metoda osy, `StreamRootChildDoc` , je metoda, která je navržena speciálně pro čtení dokumentu, který má opakující se `Child` element.  
  
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
  
 V tomto příkladu je zdrojový dokument velmi malý. Nicméně i v případě, že existovaly miliony `Child` prvků, by tento příklad měl stále malou zátěž paměti.  
