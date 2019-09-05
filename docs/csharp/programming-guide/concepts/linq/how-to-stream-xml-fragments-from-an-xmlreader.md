---
title: 'Postupy: Streamování fragmentů XML z objektuC#XmlReader ()'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e5aeb5111931ff6a35a3b7806abc24e0fbbf9621
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253294"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="7958e-102">Postupy: Streamování fragmentů XML z objektuC#XmlReader ()</span><span class="sxs-lookup"><span data-stu-id="7958e-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="7958e-103">V případě potřeby zpracování velkých souborů XML nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="7958e-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="7958e-104">Toto téma ukazuje, jak streamovat fragmenty <xref:System.Xml.XmlReader>pomocí.</span><span class="sxs-lookup"><span data-stu-id="7958e-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="7958e-105">Jedním z nejúčinnějších způsobů, jak použít <xref:System.Xml.XmlReader> ke čtení <xref:System.Xml.Linq.XElement> objektů, je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="7958e-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="7958e-106">Metoda Axis obvykle vrací kolekci <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jako je například, jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7958e-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="7958e-107">V metodě vlastní osy po vytvoření fragmentu XML voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody vraťte kolekci pomocí. `yield return`</span><span class="sxs-lookup"><span data-stu-id="7958e-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="7958e-108">To poskytuje sémantiku pro odložené provádění vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="7958e-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="7958e-109">Při vytváření stromu XML z <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader> musí být umístěn na elementu.</span><span class="sxs-lookup"><span data-stu-id="7958e-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="7958e-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda se nevrátí, dokud nepřečetla uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="7958e-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="7958e-111">Chcete-li vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>objektu, umístit čtenáře na uzel, který chcete převést <xref:System.Xml.Linq.XElement> na strom <xref:System.Xml.Linq.XElement> , a poté vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="7958e-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="7958e-112">Téma [postupy: Streamování fragmentů XML s přístupem k informacímC#hlavičky](./how-to-stream-xml-fragments-with-access-to-header-information.md) () obsahuje informace a příklad, jak streamovat složitější dokument.</span><span class="sxs-lookup"><span data-stu-id="7958e-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="7958e-113">Téma [postupy: Transformace streamování velkých dokumentů XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci extrémně velkých dokumentů XML při zachování malých nároků na paměť.</span><span class="sxs-lookup"><span data-stu-id="7958e-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7958e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7958e-114">Example</span></span>  
 <span data-ttu-id="7958e-115">Tento příklad vytvoří vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="7958e-115">This example creates a custom axis method.</span></span> <span data-ttu-id="7958e-116">Dotaz můžete vytvořit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocí dotazu.</span><span class="sxs-lookup"><span data-stu-id="7958e-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="7958e-117">Vlastní metoda osy, `StreamRootChildDoc`, je metoda, která je navržena speciálně pro čtení dokumentu, který má opakující `Child` se element.</span><span class="sxs-lookup"><span data-stu-id="7958e-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="7958e-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7958e-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="7958e-119">V tomto příkladu je zdrojový dokument velmi malý.</span><span class="sxs-lookup"><span data-stu-id="7958e-119">In this example, the source document is very small.</span></span> <span data-ttu-id="7958e-120">Nicméně i v případě, že existovaly `Child` miliony prvků, by tento příklad měl stále malou zátěž paměti.</span><span class="sxs-lookup"><span data-stu-id="7958e-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  