---
title: Jak streamovat fragmenty XML z xmlreaderu (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714658"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Jak streamovat fragmenty XML z xmlreaderu (C#)

Pokud je nutné zpracovat velké soubory XML, nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak <xref:System.Xml.XmlReader>streamovat fragmenty pomocí aplikace .  
  
 Jedním z nejúčinnějších způsobů <xref:System.Xml.XmlReader> použití <xref:System.Xml.Linq.XElement> ke čtení objektů je napsat vlastní metodu vlastní osy. Metoda osy obvykle vrací <xref:System.Collections.Generic.IEnumerable%601> kolekci, <xref:System.Xml.Linq.XElement>například , jak je znázorněno v příkladu v tomto tématu. Ve vlastní metodě axis po vytvoření fragmentu <xref:System.Xml.Linq.XNode.ReadFrom%2A> XML voláním `yield return`metody vraťte kolekci pomocí . To poskytuje odložené spuštění sémantiku vlastní metody osy.  
  
 Při vytváření stromu XML <xref:System.Xml.XmlReader> z <xref:System.Xml.XmlReader> objektu musí být umístěn na elementu. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nevrátí, dokud má přečíst close tag prvku.  
  
 Pokud chcete vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístěte čtenáře na uzel, který <xref:System.Xml.Linq.XElement> chcete převést <xref:System.Xml.Linq.XElement> na strom, a potom vytvořit objekt.  
  
Téma [Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.
  
 Téma [Jak provádět streamování transformace velkých dokumentů XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ do XML transformovat extrémně velké dokumenty XML při zachování malé nároky na paměť.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní metodu osy. Můžete dotaz pomocí dotazu LINQ. Metoda vlastní osy , je metoda, `StreamRootChildDoc`která je navržena `Child` speciálně pro čtení dokumentu, který má opakující se prvek.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
bbb  
ccc  
```  
  
 V tomto příkladu je zdrojový dokument velmi malý. Však i v případě, že byly miliony `Child` prvků, tento příklad by stále malé paměti stopy.  
