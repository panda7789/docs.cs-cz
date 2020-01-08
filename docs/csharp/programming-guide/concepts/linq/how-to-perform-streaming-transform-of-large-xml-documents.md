---
title: Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 86b74534635dcca7e8c7f94873abcb50ea7c4d2b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345816"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="6ecfc-102">Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování</span><span class="sxs-lookup"><span data-stu-id="6ecfc-102">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="6ecfc-103">Někdy je nutné transformovat velké soubory XML a napsat aplikaci tak, aby paměťové nároky aplikace byly předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="6ecfc-104">Pokud se pokusíte naplnit strom XML s velmi velkým souborem XML, využití paměti bude úměrné velikosti souboru (to znamená nadměrné).</span><span class="sxs-lookup"><span data-stu-id="6ecfc-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="6ecfc-105">Proto byste měli místo toho použít metodu streamování.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="6ecfc-106">Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="6ecfc-107">Některé standardní operátory pro dotazování, jako je například <xref:System.Linq.Enumerable.OrderBy%2A>, iterují jejich zdroj, shromažďují všechna data, řadí je a nakonec vydávají první položku v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="6ecfc-108">Všimněte si, že pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si u své aplikace uchovávat malý objem paměti.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="6ecfc-109">I v případě, že použijete techniku popsanou v tématu [postup streamování fragmentů XML sC#přístupem k informacím hlavičky ()](./how-to-stream-xml-fragments-with-access-to-header-information.md), pokud se pokusíte sestavit strom XML obsahující transformovaný dokument, využití paměti bude příliš Skvělé.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-109">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="6ecfc-110">Existují dva hlavní přístupy.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-110">There are two main approaches.</span></span> <span data-ttu-id="6ecfc-111">Jednou z možností je použít odložené zpracování vlastností <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="6ecfc-112">Dalším přístupem je vytvoření <xref:System.Xml.XmlWriter>a použití možností [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k zápisu prvků do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="6ecfc-113">Toto téma ukazuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ecfc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ecfc-114">Example</span></span>  
 <span data-ttu-id="6ecfc-115">Následující příklad je sestaven na příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacím hlavičkyC#()](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="6ecfc-115">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="6ecfc-116">V tomto příkladu se k streamování výstupu používá funkce odloženého spuštění <xref:System.Xml.Linq.XStreamingElement>.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="6ecfc-117">Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="6ecfc-118">Všimněte si, že vlastní osa (`StreamCustomerItem`) je specificky zapsána, takže očekává dokument, který obsahuje prvky `Customer`, `Name`a `Item` a že tyto prvky budou uspořádány jako v následujícím dokumentu source. XML.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="6ecfc-119">Robustnější implementace by ale mohla být připravená analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="6ecfc-120">Následuje zdrojový dokument source. XML:</span><span class="sxs-lookup"><span data-stu-id="6ecfc-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="6ecfc-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6ecfc-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6ecfc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ecfc-122">Example</span></span>  
<span data-ttu-id="6ecfc-123">Následující příklad také sestaví na příkladu v tématu [jak streamovat fragmenty XML s přístupem k informacímC#hlavičky ()](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="6ecfc-123">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="6ecfc-124">Tento příklad používá schopnost [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k zápisu prvků do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="6ecfc-125">Tento příklad může transformovat velmi velký dokument při zachování malých objemů paměti.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="6ecfc-126">Všimněte si, že vlastní osa (`StreamCustomerItem`) je specificky zapsána, takže očekává dokument, který obsahuje prvky `Customer`, `Name`a `Item` a že tyto prvky budou uspořádány jako v následujícím dokumentu source. XML.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="6ecfc-127">Robustnější implementace však buď ověří zdrojový dokument s XSD, nebo by bylo připraveno analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="6ecfc-128">Tento příklad používá stejný zdrojový dokument, source. XML, jako předchozí příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="6ecfc-129">Vytvoří také přesně stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="6ecfc-130">Při použití <xref:System.Xml.Linq.XStreamingElement> pro streamování je výstupní soubor XML preferovaný před zápisem do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ecfc-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="6ecfc-131">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6ecfc-131">This code produces the following output:</span></span>  
  
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
  