---
title: Jak provést streamování transformace velkých dokumentů XML (C#)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 9eb2e832f798e550ef3b534b0c9a0e3416378b43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169101"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="37105-102">Jak provést streamování transformace velkých dokumentů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="37105-102">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="37105-103">Někdy budete muset transformovat velké soubory XML a zapsat aplikaci tak, aby nároky na paměť aplikace je předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="37105-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="37105-104">Pokud se pokusíte naplnit strom XML velmi velkým souborem XML, bude využití paměti úměrné velikosti souboru (to znamená nadměrné).</span><span class="sxs-lookup"><span data-stu-id="37105-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="37105-105">Proto byste měli místo toho použít techniku streamování.</span><span class="sxs-lookup"><span data-stu-id="37105-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="37105-106">Techniky streamování jsou nejvhodnější v situacích, kdy je třeba zpracovat zdrojový dokument pouze jednou a prvky můžete zpracovat v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="37105-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="37105-107">Některé standardní operátory <xref:System.Linq.Enumerable.OrderBy%2A>dotazů, například , iterate jejich zdroj, shromažďovat všechna data, seřadit a nakonec výnos první položku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="37105-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="37105-108">Všimněte si, že pokud použijete operátor dotazu, který zhmotní jeho zdroj před získávání první položky, nezachováte malé nároky na paměť pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37105-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="37105-109">I v případě, že použijete techniku popsanou v [jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#),](./how-to-stream-xml-fragments-with-access-to-header-information.md)pokud se pokusíte sestavit strom XML, který obsahuje transformovaný dokument, využití paměti bude příliš velké.</span><span class="sxs-lookup"><span data-stu-id="37105-109">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="37105-110">Existují dva hlavní přístupy.</span><span class="sxs-lookup"><span data-stu-id="37105-110">There are two main approaches.</span></span> <span data-ttu-id="37105-111">Jedním z přístupů je použití <xref:System.Xml.Linq.XStreamingElement>odložených vlastností zpracování .</span><span class="sxs-lookup"><span data-stu-id="37105-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="37105-112">Dalším přístupem je <xref:System.Xml.XmlWriter>vytvoření a použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] možností zápisu <xref:System.Xml.XmlWriter>prvků do rozhraní .</span><span class="sxs-lookup"><span data-stu-id="37105-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="37105-113">Toto téma ukazuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="37105-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37105-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="37105-114">Example</span></span>  
 <span data-ttu-id="37105-115">Následující příklad vychází z příkladu v [části Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#).](./how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="37105-115">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="37105-116">Tento příklad používá možnosti <xref:System.Xml.Linq.XStreamingElement> odložené spuštění k streamování výstupu.</span><span class="sxs-lookup"><span data-stu-id="37105-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="37105-117">Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="37105-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="37105-118">Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="37105-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="37105-119">Robustnější implementace by však byla připravena analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="37105-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="37105-120">Následuje zdrojový dokument Source.xml:</span><span class="sxs-lookup"><span data-stu-id="37105-120">The following is the source document, Source.xml:</span></span>  
  
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
  
 <span data-ttu-id="37105-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="37105-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="37105-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="37105-122">Example</span></span>  
<span data-ttu-id="37105-123">Následující příklad také vychází z příkladu v [části Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#).](./how-to-stream-xml-fragments-with-access-to-header-information.md)</span><span class="sxs-lookup"><span data-stu-id="37105-123">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="37105-124">Tento příklad používá [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] schopnost psát prvky do . <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="37105-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="37105-125">Tento příklad může transformovat velmi velký dokument při zachování malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="37105-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="37105-126">Všimněte si,`StreamCustomerItem`že vlastní osa ( ) je `Customer` `Name`specificky `Item` napsána tak, že očekává dokument, který má , , a prvky a že tyto prvky budou uspořádány jako v následujícím dokumentu Source.xml.</span><span class="sxs-lookup"><span data-stu-id="37105-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="37105-127">Robustnější implementace by však buď ověřit zdrojový dokument s XSD, nebo by byla připravena analyzovat neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="37105-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="37105-128">Tento příklad používá stejný zdrojový dokument Source.xml jako předchozí příklad v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="37105-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="37105-129">Také produkuje přesně stejný výstup.</span><span class="sxs-lookup"><span data-stu-id="37105-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="37105-130">Použití <xref:System.Xml.Linq.XStreamingElement> pro streamování výstupního XML je <xref:System.Xml.XmlWriter>upřednostňováno před zápisem do .</span><span class="sxs-lookup"><span data-stu-id="37105-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="37105-131">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="37105-131">This code produces the following output:</span></span>  
  
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
  