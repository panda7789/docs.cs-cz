---
title: Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712387"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="57026-102">Jak streamovat fragmenty XML s přístupem k informacím záhlaví (C#)</span><span class="sxs-lookup"><span data-stu-id="57026-102">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="57026-103">Někdy budete muset číst libovolně velké soubory XML a zapsat aplikaci tak, aby nároky na paměť aplikace je předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="57026-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="57026-104">Pokud se pokusíte naplnit strom XML velkým souborem XML, bude využití paměti úměrné velikosti souboru , tj.</span><span class="sxs-lookup"><span data-stu-id="57026-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="57026-105">Proto byste měli místo toho použít techniku streamování.</span><span class="sxs-lookup"><span data-stu-id="57026-105">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="57026-106">Jednou z možností je <xref:System.Xml.XmlReader>napsat aplikaci pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="57026-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="57026-107">Můžete však chtít použít LINQ k dotazování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="57026-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="57026-108">Pokud se jedná o tento případ, můžete napsat vlastní metodu vlastní osy.</span><span class="sxs-lookup"><span data-stu-id="57026-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="57026-109">Další informace naleznete [v tématu Jak napsat metodu osy LINQ do XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="57026-109">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="57026-110">Chcete-li napsat vlastní metodu osy, <xref:System.Xml.XmlReader> napište malou metodu, která používá ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="57026-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="57026-111">Metoda pak <xref:System.Xml.Linq.XNode.ReadFrom%2A>volá , který <xref:System.Xml.XmlReader> čte z a konkretizovat xml fragment.</span><span class="sxs-lookup"><span data-stu-id="57026-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="57026-112">Potom výnosy každý `yield return` fragment až do metody, která je výčet vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="57026-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="57026-113">Potom můžete psát dotazy LINQ na vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="57026-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="57026-114">Techniky streamování jsou nejvhodnější v situacích, kdy je třeba zpracovat zdrojový dokument pouze jednou a prvky můžete zpracovat v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="57026-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="57026-115">Některé standardní operátory <xref:System.Linq.Enumerable.OrderBy%2A>dotazů, například , iterate jejich zdroj, shromažďovat všechna data, seřadit a nakonec výnos první položku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="57026-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="57026-116">Pokud použijete operátor dotazu, který zhmotní jeho zdroj před výnosem první položky, nezachováte malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="57026-116">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57026-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="57026-117">Example</span></span>  

<span data-ttu-id="57026-118">Někdy je problém trochu zajímavější.</span><span class="sxs-lookup"><span data-stu-id="57026-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="57026-119">V následujícím dokumentu XML musí příjemce metody vlastní osy také znát jméno zákazníka, ke kterému každá položka patří.</span><span class="sxs-lookup"><span data-stu-id="57026-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="57026-120">Přístup, který tento příklad používá, je také sledovat informace o tomto záhlaví, uložit informace záhlaví a potom vytvořit malý strom XML, který obsahuje informace záhlaví a podrobnosti, které jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="57026-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="57026-121">Metoda osy pak dává tento nový, malý strom XML.</span><span class="sxs-lookup"><span data-stu-id="57026-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="57026-122">Dotaz pak má přístup k informacím záhlaví, stejně jako podrobné informace.</span><span class="sxs-lookup"><span data-stu-id="57026-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="57026-123">Tento přístup má malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="57026-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="57026-124">Jako každý detail XML fragment je výnosný, žádné odkazy jsou uchovávány na předchozí fragment a je k dispozici pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="57026-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="57026-125">Tato technika vytvoří mnoho objektů s krátkou životností na haldě.</span><span class="sxs-lookup"><span data-stu-id="57026-125">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="57026-126">Následující příklad ukazuje, jak implementovat a používat vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="57026-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="57026-127">Tato vlastní osa je napsána tak, `Name`že `Item` očekává dokument, který má `Customer`, , `Source.xml` a prvky a že tyto prvky budou uspořádány jako ve výše uvedeném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="57026-127">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="57026-128">Jedná se o zjednodušující implementaci.</span><span class="sxs-lookup"><span data-stu-id="57026-128">It is a simplistic implementation.</span></span> <span data-ttu-id="57026-129">Robustnější implementace by byla připravena k analýzě neplatného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="57026-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="57026-130">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="57026-130">This code produces the following output:</span></span>  
  
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
