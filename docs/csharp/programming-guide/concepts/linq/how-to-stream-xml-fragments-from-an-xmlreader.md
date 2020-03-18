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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="9c568-102">Jak streamovat fragmenty XML z xmlreaderu (C#)</span><span class="sxs-lookup"><span data-stu-id="9c568-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="9c568-103">Pokud je nutné zpracovat velké soubory XML, nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="9c568-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="9c568-104">Toto téma ukazuje, jak <xref:System.Xml.XmlReader>streamovat fragmenty pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="9c568-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="9c568-105">Jedním z nejúčinnějších způsobů <xref:System.Xml.XmlReader> použití <xref:System.Xml.Linq.XElement> ke čtení objektů je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="9c568-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="9c568-106">Metoda osy obvykle vrací <xref:System.Collections.Generic.IEnumerable%601> kolekci, <xref:System.Xml.Linq.XElement>například , jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9c568-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="9c568-107">Ve vlastní metodě axis po vytvoření fragmentu <xref:System.Xml.Linq.XNode.ReadFrom%2A> XML voláním `yield return`metody vraťte kolekci pomocí .</span><span class="sxs-lookup"><span data-stu-id="9c568-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="9c568-108">To poskytuje odložené spuštění sémantiku vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="9c568-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="9c568-109">Při vytváření stromu XML <xref:System.Xml.XmlReader> z <xref:System.Xml.XmlReader> objektu musí být umístěn na elementu.</span><span class="sxs-lookup"><span data-stu-id="9c568-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="9c568-110">Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nevrátí, dokud má přečíst close tag prvku.</span><span class="sxs-lookup"><span data-stu-id="9c568-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="9c568-111">Pokud chcete vytvořit částečný strom, můžete vytvořit instanci <xref:System.Xml.XmlReader>, umístěte čtenáře na uzel, který <xref:System.Xml.Linq.XElement> chcete převést <xref:System.Xml.Linq.XElement> na strom, a potom vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="9c568-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="9c568-112">Téma [Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad, jak streamovat složitější dokument.</span><span class="sxs-lookup"><span data-stu-id="9c568-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="9c568-113">Téma [Jak provádět streamování transformace velkých dokumentů XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ do XML transformovat extrémně velké dokumenty XML při zachování malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="9c568-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c568-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c568-114">Example</span></span>  
 <span data-ttu-id="9c568-115">Tento příklad vytvoří vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="9c568-115">This example creates a custom axis method.</span></span> <span data-ttu-id="9c568-116">Můžete dotaz pomocí dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="9c568-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="9c568-117">Metoda vlastní osy , je metoda, `StreamRootChildDoc`která je navržena `Child` speciálně pro čtení dokumentu, který má opakující se prvek.</span><span class="sxs-lookup"><span data-stu-id="9c568-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="9c568-118">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9c568-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="9c568-119">V tomto příkladu je zdrojový dokument velmi malý.</span><span class="sxs-lookup"><span data-stu-id="9c568-119">In this example, the source document is very small.</span></span> <span data-ttu-id="9c568-120">Však i v případě, že byly miliony `Child` prvků, tento příklad by stále malé paměti stopy.</span><span class="sxs-lookup"><span data-stu-id="9c568-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
