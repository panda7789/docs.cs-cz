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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="94c64-104">Postup streamování fragmentů XML ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="94c64-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="94c64-105">V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="94c64-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="94c64-106">Toto téma ukazuje, jak streamovat fragmenty pomocí <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="94c64-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="94c64-107">Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení <xref:System.Xml.Linq.XElement> objektů, je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="94c64-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="94c64-108">Metoda Axis obvykle vrací kolekci, jako je například <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="94c64-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="94c64-109">V metodě vlastní osy po vytvoření fragmentu XML voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody vraťte kolekci pomocí `yield return` .</span><span class="sxs-lookup"><span data-stu-id="94c64-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="94c64-110">To poskytuje sémantiku pro odložené provádění vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="94c64-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="94c64-111">Při vytváření stromu XML z <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader> musí být umístěn na elementu.</span><span class="sxs-lookup"><span data-stu-id="94c64-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="94c64-112"><xref:System.Xml.Linq.XNode.ReadFrom%2A>Metoda se nevrátí, dokud nepřečetla uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="94c64-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="94c64-113">Chcete-li vytvořit částečný strom, můžete vytvořit instanci objektu <xref:System.Xml.XmlReader> , umístit čtenáře na uzel, který chcete převést na <xref:System.Xml.Linq.XElement> strom, a poté vytvořit <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="94c64-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="94c64-114">Téma, [jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.</span><span class="sxs-lookup"><span data-stu-id="94c64-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="94c64-115">Téma, [Jak provést transformaci velkých dokumentů XML (C#) pomocí streamování](./how-to-perform-streaming-transform-of-large-xml-documents.md) , obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.</span><span class="sxs-lookup"><span data-stu-id="94c64-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94c64-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="94c64-116">Example</span></span>  
 <span data-ttu-id="94c64-117">Tento příklad vytvoří vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="94c64-117">This example creates a custom axis method.</span></span> <span data-ttu-id="94c64-118">Můžete se k němu dotázat pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="94c64-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="94c64-119">Vlastní metoda osy, `StreamRootChildDoc` , je metoda, která je navržena speciálně pro čtení dokumentu, který má opakující se `Child` element.</span><span class="sxs-lookup"><span data-stu-id="94c64-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="94c64-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="94c64-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="94c64-121">V tomto příkladu je zdrojový dokument velmi malý.</span><span class="sxs-lookup"><span data-stu-id="94c64-121">In this example, the source document is very small.</span></span> <span data-ttu-id="94c64-122">Nicméně i v případě, že existovaly miliony `Child` prvků, by tento příklad měl stále malou zátěž paměti.</span><span class="sxs-lookup"><span data-stu-id="94c64-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
