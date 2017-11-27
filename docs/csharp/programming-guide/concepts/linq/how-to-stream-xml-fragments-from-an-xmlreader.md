---
title: 'Postupy: Stream fragmenty XML z XmlReader (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2fe1bc1122900bab6f65db785027add4e0a8e4f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Postupy: Stream fragmenty XML z XmlReader (C#)
Až budete mít ke zpracování velkých souborů XML, nemusí být vhodný načíst celý strom XML do paměti. Toto téma ukazuje, jak k vysílání datového proudu fragmenty pomocí <xref:System.Xml.XmlReader>.  
  
 Jedním z nejúčinnějších způsobů, jak používat <xref:System.Xml.XmlReader> číst <xref:System.Xml.Linq.XElement> objektů je napsat vlastní metodu vlastní osy. Metodu osy, jako obvykle vrátí kolekci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy, po vytvoření XML fragment voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda, vrátí kolekce používá `yield return`. To poskytuje sémantiku odložené provedení metodu vlastní osy.  
  
 Když vytvoříte strom XML z <xref:System.Xml.XmlReader> objekt, <xref:System.Xml.XmlReader> musí být umístěn v elementu. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nevrátí před přečtením značka ukončení elementu.  
  
 Pokud chcete vytvořit částečné stromové struktury, můžete vytvořit instanci <xref:System.Xml.XmlReader>, pozice čtenáře na uzlu, který chcete převést na <xref:System.Xml.Linq.XElement> stromu a pak vytvořte <xref:System.Xml.Linq.XElement> objektu.  
  
 Téma [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad o tom, jak stream složitější dokumentu.  
  
 Téma [postup: provedení vysílání datového proudu transformace z velké dokumentů XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití technologie LINQ to XML k transformaci velmi velký dokumentů XML při zachování nároků paměti.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vlastní osy metoda. Se můžete dotazovat pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Metodu vlastní osy `StreamRootChildDoc`, je metoda, která je určená speciálně pro čtení dokumentu, který má opakující se `Child` elementu.  
  
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
  
 V tomto příkladu jsou velmi malé zdrojový dokument. Ale i v případě, že bylo miliony `Child` elementy, v tomto příkladu by mít stále malou paměťovou zátěž.  
  
## <a name="see-also"></a>Viz také  
 [Analýza kódu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
