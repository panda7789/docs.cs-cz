---
title: "Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07fe45bb54c0d8b867cd3ae03fc3ed940243a538
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="b9d9e-102">Postupy: Stream fragmenty kódu XML se přístup k informacím o záhlaví (C#)</span><span class="sxs-lookup"><span data-stu-id="b9d9e-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="b9d9e-103">Někdy je nutné ke čtení libovolně velké soubory XML a zapisovat vaše aplikace tak, aby nároky na paměť pro aplikace je předvídatelný.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="b9d9e-104">Pokud se pokusíte strom XML naplnění velký soubor XML, bude vaše využití paměti velikosti souboru – to znamená, nadměrné.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="b9d9e-105">Proto byste měli místo toho používat streamování techniku.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="b9d9e-106">Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b9d9e-107">Ale můžete chtít použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="b9d9e-108">Pokud je to tento případ, můžete napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="b9d9e-109">Další informace najdete v tématu [postupy: zápis LINQ metodě osy XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="b9d9e-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="b9d9e-110">Zápis způsob osy, zápis malých metody, která používá <xref:System.Xml.XmlReader> číst uzlů, dokud nebude dosaženo jednoho z uzlů, které vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="b9d9e-111">Pak zavolá metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A>, který čte z <xref:System.Xml.XmlReader> a vytvoří XML fragment.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="b9d9e-112">Potom dává každý fragment prostřednictvím `yield return` na metodu, která je výčet metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="b9d9e-113">Poté můžete napsat dotazů LINQ na metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="b9d9e-114">Streamování techniky nejlépe použity v situacích, kdy je potřeba zpracovat zdrojový dokument jenom jednou a může zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="b9d9e-115">Některé standardní operátory dotazů, jako například <xref:System.Linq.Enumerable.OrderBy%2A>iteraci zdrojových, shromáždit všechna data, řazení ji a nakonec yield první položky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="b9d9e-116">Všimněte si, pokud používáte operátor dotazu, který bude realizována zdrojem před je první položka, nebude zachovali malou paměťovou zátěž.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9d9e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9d9e-117">Example</span></span>  
 <span data-ttu-id="b9d9e-118">Někdy problém získá jen málo další zajímavé.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="b9d9e-119">V následujícím dokumentu XML má příjemce metodu vlastní osy také znát název zákazníka, které patří každou položku.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="b9d9e-120">Přístup, který má v tomto příkladu je také sledovat informace hlavičky, uložit informace ze záhlaví a následně vytvořit malé stromu XML, který obsahuje informace v záhlaví a podrobností, která jsou vytváření výčtu.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="b9d9e-121">Metoda osy poskytuje pak tento nový, malé strom XML.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="b9d9e-122">Dotaz pak má přístup k informace hlavičky, jakož i podrobné informace.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="b9d9e-123">Tento přístup má malou paměťovou zátěž.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="b9d9e-124">Každý fragment XML podrobností, je vhodné, jsou uchovány žádné odkazy na předchozí fragment, a je k dispozici pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="b9d9e-125">Všimněte si, že tento postup vytvoří mnoho zkrátí objektů v haldě.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="b9d9e-126">Následující příklad ukazuje, jak implementovat a použít vlastní osy metodu, která datové proudy fragmenty XML ze souboru určeného identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="b9d9e-127">Tato vlastní osy je speciálně tak, aby se očekává, že dokument, který má `Customer`, `Name`, a `Item` elementy a aby tyto prvky se být uspořádány jako výše `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="b9d9e-128">Je zneužívající vlastností prohlížeče implementace.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-128">It is a simplistic implementation.</span></span> <span data-ttu-id="b9d9e-129">Robustnější implementace by připravený k analýze neplatný dokument.</span><span class="sxs-lookup"><span data-stu-id="b9d9e-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="b9d9e-130">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b9d9e-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9d9e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d9e-131">See Also</span></span>  
 [<span data-ttu-id="b9d9e-132">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="b9d9e-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
