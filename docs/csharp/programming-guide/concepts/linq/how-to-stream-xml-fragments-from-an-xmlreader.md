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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="aeaf9-102">Postup streamování fragmentů XML z objektu XmlReaderC#()</span><span class="sxs-lookup"><span data-stu-id="aeaf9-102">How to stream XML fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="aeaf9-103">V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="aeaf9-104">Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="aeaf9-105">Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení objektů <xref:System.Xml.Linq.XElement>, je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="aeaf9-106">Metoda Axis obvykle vrací kolekci, například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="aeaf9-107">V metodě vlastní osy po vytvoření fragmentu XML voláním metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> vraťte kolekci pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="aeaf9-108">To poskytuje sémantiku pro odložené provádění vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="aeaf9-109">Při vytváření stromu XML z objektu <xref:System.Xml.XmlReader> musí být <xref:System.Xml.XmlReader> umístěn na elementu.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="aeaf9-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nevrátí, dokud nepřečetla uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="aeaf9-111">Chcete-li vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístit čtecí modul na uzel, který chcete převést na <xref:System.Xml.Linq.XElement> stromu, a poté vytvořit objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="aeaf9-112">Téma, [jak streamovat fragmenty XML s přístupem k informacím hlavičkyC#()](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="aeaf9-113">Téma, [Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování](./how-to-perform-streaming-transform-of-large-xml-documents.md) , obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeaf9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeaf9-114">Example</span></span>  
 <span data-ttu-id="aeaf9-115">Tento příklad vytvoří vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-115">This example creates a custom axis method.</span></span> <span data-ttu-id="aeaf9-116">Můžete se k němu dotázat pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="aeaf9-117">Vlastní metoda osy, `StreamRootChildDoc`, je metoda, která je určena specificky pro čtení dokumentu, který má opakující se `Child` element.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="aeaf9-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="aeaf9-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="aeaf9-119">V tomto příkladu je zdrojový dokument velmi malý.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-119">In this example, the source document is very small.</span></span> <span data-ttu-id="aeaf9-120">Nicméně i v případě, že existovaly miliony `Child` prvků, bude mít tento příklad pořád malou paměť.</span><span class="sxs-lookup"><span data-stu-id="aeaf9-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  