---
title: Postup při streamování fragmentů XML s přístupem k informacímC#hlavičky ()
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712387"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="df0e5-102">Postup při streamování fragmentů XML s přístupem k informacímC#hlavičky ()</span><span class="sxs-lookup"><span data-stu-id="df0e5-102">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="df0e5-103">Někdy je nutné číst libovolně velké soubory XML a napsat aplikaci tak, aby paměti aplikace byly předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="df0e5-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="df0e5-104">Pokud se pokusíte naplnit strom XML velkým souborem XML, využití paměti bude úměrné velikosti souboru, tedy nadměrné.</span><span class="sxs-lookup"><span data-stu-id="df0e5-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="df0e5-105">Proto byste měli místo toho použít metodu streamování.</span><span class="sxs-lookup"><span data-stu-id="df0e5-105">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="df0e5-106">Jednou z možností je napsat aplikaci pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="df0e5-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="df0e5-107">Můžete však chtít použít LINQ k dotazování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="df0e5-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="df0e5-108">Pokud se jedná o tento případ, můžete napsat vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="df0e5-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="df0e5-109">Další informace najdete v tématu [Postup zápisu metody osy LINQ to XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="df0e5-109">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="df0e5-110">Chcete-li napsat vlastní metodu osy, napíšete malou metodu, která používá <xref:System.Xml.XmlReader> ke čtení uzlů, dokud nedosáhne jednoho z uzlů, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="df0e5-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="df0e5-111">Metoda pak zavolá <xref:System.Xml.Linq.XNode.ReadFrom%2A>, které čtou z <xref:System.Xml.XmlReader> a vytvoří instanci fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="df0e5-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="df0e5-112">Následně výsledkem každého fragmentu `yield return` metoda, která vytváří výčet vlastní metody osy.</span><span class="sxs-lookup"><span data-stu-id="df0e5-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="df0e5-113">Pak můžete napsat dotazy LINQ na vlastní metodu osy.</span><span class="sxs-lookup"><span data-stu-id="df0e5-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="df0e5-114">Techniky streamování se nejlépe aplikují v situacích, kdy potřebujete zpracovat zdrojový dokument jenom jednou, a můžete zpracovat elementy v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="df0e5-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="df0e5-115">Některé standardní operátory pro dotazování, jako je například <xref:System.Linq.Enumerable.OrderBy%2A>, iterují jejich zdroj, shromažďují všechna data, řadí je a nakonec vydávají první položku v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="df0e5-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="df0e5-116">Pokud použijete operátor dotazu, který materializuje svůj zdroj před tím, než zadáte první položku, nebudete si uchovávat malý objem paměti.</span><span class="sxs-lookup"><span data-stu-id="df0e5-116">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0e5-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="df0e5-117">Example</span></span>  

<span data-ttu-id="df0e5-118">Někdy je problém jenom trochu zajímavější.</span><span class="sxs-lookup"><span data-stu-id="df0e5-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="df0e5-119">V následujícím dokumentu XML musí příjemce vlastní metody osy také znát název zákazníka, ke kterému každá položka patří.</span><span class="sxs-lookup"><span data-stu-id="df0e5-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="df0e5-120">Přístup v tomto příkladu je také sledován pro tyto informace hlavičky, uložení informací v hlavičce a následné sestavení malého stromu XML, který obsahuje jak informace v hlavičce, tak i podrobnosti, které provádíte ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="df0e5-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="df0e5-121">Metoda Axis pak tento nový malý strom XML.</span><span class="sxs-lookup"><span data-stu-id="df0e5-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="df0e5-122">Dotaz pak má přístup k informacím v hlavičce a také k podrobným informacím.</span><span class="sxs-lookup"><span data-stu-id="df0e5-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="df0e5-123">Tento přístup má malé nároky na paměť.</span><span class="sxs-lookup"><span data-stu-id="df0e5-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="df0e5-124">Vzhledem k tomu, že se přestanou fragmenty XML, nezachovají se žádné odkazy na předchozí fragment a je k dispozici pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="df0e5-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="df0e5-125">Tato technika vytvoří mnoho krátkodobých objektů v haldě.</span><span class="sxs-lookup"><span data-stu-id="df0e5-125">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="df0e5-126">Následující příklad ukazuje, jak implementovat a použít vlastní metodu osy, která streamuje fragmenty XML ze souboru určeného identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="df0e5-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="df0e5-127">Tato vlastní osa je zapsána tak, že očekává dokument, který má `Customer`, `Name`a `Item` prvky a že tyto prvky budou uspořádány jako v předchozím `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="df0e5-127">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="df0e5-128">Jedná se o zjednodušený implementaci.</span><span class="sxs-lookup"><span data-stu-id="df0e5-128">It is a simplistic implementation.</span></span> <span data-ttu-id="df0e5-129">Robustnější implementace by se připravila k analýze neplatného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="df0e5-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="df0e5-130">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="df0e5-130">This code produces the following output:</span></span>  
  
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
