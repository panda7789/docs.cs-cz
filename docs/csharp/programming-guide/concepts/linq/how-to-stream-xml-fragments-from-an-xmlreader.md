---
title: 'Postupy: Stream fragmentů XML ze třídy XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 0c34b9aeb5cda61c13045487dee6ab15e55314e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693990"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Postupy: Stream fragmentů XML ze třídy XmlReader (C#)
Až budete mít ke zpracování velkých souborů XML, nemusí být možné načíst celý strom XML do paměti. Toto téma ukazuje, jak streamování fragmentů pomocí <xref:System.Xml.XmlReader>.  
  
 Jeden z nejefektivnějších způsobech použití <xref:System.Xml.XmlReader> číst <xref:System.Xml.Linq.XElement> objekty je napsat vlastní metodu vlastní osy. Metodu osy, jako obvykle vrátí kolekci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu. V metodě vlastní osy, po vytvoření XML fragment voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody, vrátí kolekci pomocí `yield return`. To poskytuje sémantiku odložené provedení metodě vlastní osy.  
  
 Při vytváření stromu XML ze <xref:System.Xml.XmlReader> objektu, <xref:System.Xml.XmlReader> musí být umístěna na elementu. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nevrací před přečtením uzavíracím tagem elementu.  
  
 Pokud chcete vytvořit částečné stromové struktury, můžete vytvořit instanci <xref:System.Xml.XmlReader>, pozice čtenáře na uzlu, který chcete převést na <xref:System.Xml.Linq.XElement> stromu a pak vytvořte <xref:System.Xml.Linq.XElement> objektu.  
  
 Téma [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad toho, jak Streamovat složitější dokumentu.  
  
 Téma [jak: Provádění datových proudů transformace z velké dokumentů XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci velmi velké dokumentů XML a přitom malá paměťové nároky.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří metodu vlastní osy. Můžete ji dotazovat s použitím [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Metoda vlastní osy `StreamRootChildDoc`, je metoda, která je navržená speciálně pro čtení dokumentu, který má s opakováním `Child` elementu.  
  
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
  
 V tomto příkladu je velmi malý zdrojovém dokumentu. Nicméně i v případě, že došlo k milionům `Child` prvky, v tomto příkladu by stále mají malé paměťové nároky.  
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
