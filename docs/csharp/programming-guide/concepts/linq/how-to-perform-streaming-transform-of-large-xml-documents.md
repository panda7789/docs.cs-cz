---
title: 'Postup: provedení streamování transformace dokumentů XML velké (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 1a12e8c0ae98be37599b05e5d63469336247d915
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325601"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="bfee6-102">Postup: provedení streamování transformace dokumentů XML velké (C#)</span><span class="sxs-lookup"><span data-stu-id="bfee6-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="bfee6-103">Někdy je nutné transformovat velkých souborů XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace je předvídatelný.</span><span class="sxs-lookup"><span data-stu-id="bfee6-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="bfee6-104">Pokud se pokusíte naplnit strom XML s velmi velký soubor XML, bude vaše využití paměti velikosti souboru (to znamená, nadměrné).</span><span class="sxs-lookup"><span data-stu-id="bfee6-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="bfee6-105">Proto byste měli místo toho používat streamování techniku.</span><span class="sxs-lookup"><span data-stu-id="bfee6-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="bfee6-106">Streamování techniky nejlépe použity v situacích, kdy je potřeba zpracovat zdrojový dokument jenom jednou a může zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="bfee6-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="bfee6-107">Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iteraci zdrojových, shromáždit všechna data, řazení ji a nakonec yield první položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bfee6-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="bfee6-108">Všimněte si, pokud používáte operátor dotazu, který bude realizována zdrojem před je první položka, nebude zachovali malou paměťovou zátěž pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bfee6-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="bfee6-109">I když používáte podle postupu popsaného v [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit strom XML obsahující transformovaná dokumentu paměti využití bude příliš velký.</span><span class="sxs-lookup"><span data-stu-id="bfee6-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="bfee6-110">Existují dva hlavní přístupy.</span><span class="sxs-lookup"><span data-stu-id="bfee6-110">There are two main approaches.</span></span> <span data-ttu-id="bfee6-111">Jeden z přístupů je použít odložené zpracování charakteristika <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="bfee6-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="bfee6-112">Další možností je vytvořit <xref:System.Xml.XmlWriter>a využívat možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zápis elementy, aby <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="bfee6-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="bfee6-113">Toto téma popisuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="bfee6-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfee6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfee6-114">Example</span></span>  
 <span data-ttu-id="bfee6-115">V následujícím příkladu je založena na příkladu v [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="bfee6-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="bfee6-116">Tento příklad používá možnosti odložené provedení <xref:System.Xml.Linq.XStreamingElement> k vysílání datového proudu výstup.</span><span class="sxs-lookup"><span data-stu-id="bfee6-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="bfee6-117">V tomto příkladu můžete převést velké dokumentu při zachování nároků paměti.</span><span class="sxs-lookup"><span data-stu-id="bfee6-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="bfee6-118">Všimněte si, že vlastní osy (`StreamCustomerItem`) je speciálně tak, aby se očekává, že dokument s `Customer`, `Name`, a `Item` prvky a aby tyto prvky uspořádány, jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="bfee6-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="bfee6-119">Robustnější implementace, by však připravený k analýze neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="bfee6-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="bfee6-120">Toto je zdrojový dokument, Source.xml:</span><span class="sxs-lookup"><span data-stu-id="bfee6-120">The following is the source document, Source.xml:</span></span>  
  
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
                        if (item != null)  
                        {  
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
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="bfee6-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bfee6-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="bfee6-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfee6-122">Example</span></span>  
 <span data-ttu-id="bfee6-123">V následujícím příkladu je taky založený na příkladu v [postup: datový proud XML fragmenty se přístup k informacím o záhlaví (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="bfee6-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="bfee6-124">Tento příklad používá funkci aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zápis elementy, aby <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="bfee6-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="bfee6-125">V tomto příkladu můžete převést velké dokumentu při zachování nároků paměti.</span><span class="sxs-lookup"><span data-stu-id="bfee6-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="bfee6-126">Všimněte si, že vlastní osy (`StreamCustomerItem`) je speciálně tak, aby se očekává, že dokument s `Customer`, `Name`, a `Item` prvky a aby tyto prvky uspořádány, jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="bfee6-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="bfee6-127">Robustnější implementace, ale by buď ověření zdrojový dokument s XSD nebo by připravené k analýze neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="bfee6-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="bfee6-128">Tento příklad používá stejný zdrojový dokument, Source.xml, jako v předchozím příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="bfee6-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="bfee6-129">Vytváří také přesně stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="bfee6-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="bfee6-130">Pomocí <xref:System.Xml.Linq.XStreamingElement> pro streamování výstup XML je upřednostňovaný přes zápis do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="bfee6-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="bfee6-131">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bfee6-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfee6-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfee6-132">See Also</span></span>  
 [<span data-ttu-id="bfee6-133">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="bfee6-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
