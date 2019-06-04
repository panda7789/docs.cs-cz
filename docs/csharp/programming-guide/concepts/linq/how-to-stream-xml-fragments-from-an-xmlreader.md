---
title: 'Postupy: Stream fragmentů XML ze třídy XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 6937a7160c83def3238c8d2fe3e2b83c996396fd
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484908"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="7cf18-102">Postupy: Stream fragmentů XML ze třídy XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="7cf18-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="7cf18-103">Až budete mít ke zpracování velkých souborů XML, nemusí být možné načíst celý strom XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="7cf18-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="7cf18-104">Toto téma ukazuje, jak streamování fragmentů pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7cf18-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="7cf18-105">Jeden z nejefektivnějších způsobech použití <xref:System.Xml.XmlReader> číst <xref:System.Xml.Linq.XElement> objekty je napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="7cf18-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="7cf18-106">Metodu osy, jako obvykle vrátí kolekci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak je znázorněno v příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="7cf18-107">V metodě vlastní osy, po vytvoření XML fragment voláním <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody, vrátí kolekci pomocí `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7cf18-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="7cf18-108">To poskytuje sémantiku odložené provedení metodě vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="7cf18-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="7cf18-109">Při vytváření stromu XML ze <xref:System.Xml.XmlReader> objektu, <xref:System.Xml.XmlReader> musí být umístěna na elementu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="7cf18-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nevrací před přečtením uzavíracím tagem elementu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="7cf18-111">Pokud chcete vytvořit částečné stromové struktury, můžete vytvořit instanci <xref:System.Xml.XmlReader>, pozice čtenáře na uzlu, který chcete převést na <xref:System.Xml.Linq.XElement> stromu a pak vytvořte <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="7cf18-112">Téma [jak: Stream fragmentů XML pomocí přístup k informacím hlavičky (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) obsahuje informace a příklad toho, jak Streamovat složitější dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="7cf18-113">Téma [jak: Provádění datových proudů transformace z velké dokumentů XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) obsahuje příklad použití LINQ to XML k transformaci velmi velké dokumentů XML a přitom malá paměťové nároky.</span><span class="sxs-lookup"><span data-stu-id="7cf18-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cf18-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cf18-114">Example</span></span>  
 <span data-ttu-id="7cf18-115">Tento příklad vytvoří metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="7cf18-115">This example creates a custom axis method.</span></span> <span data-ttu-id="7cf18-116">Můžete ji dotazovat s použitím [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="7cf18-117">Metoda vlastní osy `StreamRootChildDoc`, je metoda, která je navržená speciálně pro čtení dokumentu, který má s opakováním `Child` elementu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="7cf18-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7cf18-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="7cf18-119">V tomto příkladu je velmi malý zdrojovém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7cf18-119">In this example, the source document is very small.</span></span> <span data-ttu-id="7cf18-120">Nicméně i v případě, že došlo k milionům `Child` prvky, v tomto příkladu by stále mají malé paměťové nároky.</span><span class="sxs-lookup"><span data-stu-id="7cf18-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  