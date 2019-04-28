---
title: 'Postupy: Provedení streamované transformace velkých dokumentů XML (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 8ddd7e25cf160526b741db5769a78682970c3724
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701954"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="43338-102">Postupy: Provedení streamované transformace velkých dokumentů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="43338-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="43338-103">Někdy je nutné transformovat velké soubory XML a zápis aplikace tak, aby nároky na paměť pro aplikace předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="43338-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="43338-104">Pokud se pokusíte naplnění stromu XML pomocí velmi velkých souborů XML, využití paměti bude přímo úměrná velikosti souboru (to znamená, nadměrné).</span><span class="sxs-lookup"><span data-stu-id="43338-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="43338-105">Proto měli používat streamování technika místo.</span><span class="sxs-lookup"><span data-stu-id="43338-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="43338-106">Streamování techniky aplikují nejlépe v situacích, kde je potřeba zpracovat zdrojový dokument pouze jednou a může zpracovat prvky v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="43338-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="43338-107">Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iterovat jejich zdroj, shromáždit všechna data, seřadit a nakonec yield první položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="43338-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="43338-108">Všimněte si, že pokud použijete operátor dotazu, který bude realizována zdrojem před získávání první položka, nebudou zachovány malé paměťové nároky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="43338-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="43338-109">I když používáte podle postupu popsaného v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit stromu XML obsahující transformovaná dokument, bude příliš velké využití paměti.</span><span class="sxs-lookup"><span data-stu-id="43338-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="43338-110">Existují dva hlavní přístupy.</span><span class="sxs-lookup"><span data-stu-id="43338-110">There are two main approaches.</span></span> <span data-ttu-id="43338-111">Jedním z přístupů je použít vlastnosti odložené zpracování <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="43338-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="43338-112">Další možností je vytvořit <xref:System.Xml.XmlWriter>a s využitím možností [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapisovat elementy, které chcete <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="43338-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="43338-113">Toto téma ukazuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="43338-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43338-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="43338-114">Example</span></span>  
 <span data-ttu-id="43338-115">Následující příklad je založen na příklad v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="43338-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="43338-116">Tento příklad používá možnosti odložené provedení <xref:System.Xml.Linq.XStreamingElement> Streamovat výstup.</span><span class="sxs-lookup"><span data-stu-id="43338-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="43338-117">V tomto příkladu můžete transformovat velmi velkých dokumentů při zachování malé paměťové nároky.</span><span class="sxs-lookup"><span data-stu-id="43338-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="43338-118">Všimněte si, že vlastní osy (`StreamCustomerItem`) je konkrétně napsána tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` prvky. proto, že tyto prvky se uspořádané jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="43338-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="43338-119">Robustnější implementace by však připravit analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="43338-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="43338-120">Následuje zdrojovém dokumentu Source.xml:</span><span class="sxs-lookup"><span data-stu-id="43338-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="43338-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="43338-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="43338-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="43338-122">Example</span></span>  
 <span data-ttu-id="43338-123">Následující příklad také vytvoří v příkladu v [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="43338-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="43338-124">Tento příklad používá funkci aplikace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapisovat elementy, které chcete <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="43338-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="43338-125">V tomto příkladu můžete transformovat velmi velkých dokumentů při zachování malé paměťové nároky.</span><span class="sxs-lookup"><span data-stu-id="43338-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="43338-126">Všimněte si, že vlastní osy (`StreamCustomerItem`) je konkrétně napsána tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` prvky. proto, že tyto prvky se uspořádané jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="43338-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="43338-127">Robustnější implementaci, ale by buď ověřit zdrojový dokument s XSD nebo bude připravený k analýze neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="43338-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="43338-128">Tento příklad používá stejný zdrojový dokument Source.xml, stejně jako v předchozím příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="43338-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="43338-129">Vytvoří také přesně stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="43338-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="43338-130">Pomocí <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupním souboru XML je upřednostňované nad zápisu do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="43338-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="43338-131">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="43338-131">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43338-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43338-132">See also</span></span>

- [<span data-ttu-id="43338-133">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="43338-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
