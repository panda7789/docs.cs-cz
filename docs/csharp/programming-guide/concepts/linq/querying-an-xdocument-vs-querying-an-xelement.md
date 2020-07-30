---
title: Dotazování na XDocument a dotazování na XElement (C#)
description: Přečtěte si o rozdílech mezi dotazem na XDocument a dotazem na XElement. Přečtěte si příklady kódu, které ukazují tyto rozdíly.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300303"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="d7918-104">Dotazování na XDocument a dotazování na XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="d7918-104">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="d7918-105">Když načtete dokument prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , všimnete si, že budete muset psát dotazy trochu jinak než při načítání prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d7918-105">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="d7918-106">Porovnání XDocument. Load a XElement. Load</span><span class="sxs-lookup"><span data-stu-id="d7918-106">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="d7918-107">Když načtete dokument XML do <xref:System.Xml.Linq.XElement> Via, v <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement> kořenu stromu XML obsahuje kořenový prvek načteného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d7918-107">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="d7918-108">Nicméně když načtete stejný dokument XML do <xref:System.Xml.Linq.XDocument> Via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , kořen stromové struktury je <xref:System.Xml.Linq.XDocument> uzel a kořenový prvek načteného dokumentu je jeden povolený podřízený <xref:System.Xml.Linq.XElement> uzel <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="d7918-108">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="d7918-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Osy pracují relativně ke kořenovému uzlu.</span><span class="sxs-lookup"><span data-stu-id="d7918-109">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="d7918-110">Tento první příklad načte strom XML pomocí <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7918-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="d7918-111">Pak se dotazuje na podřízené prvky kořenového adresáře stromu.</span><span class="sxs-lookup"><span data-stu-id="d7918-111">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="d7918-112">Jak je očekáváno, tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d7918-112">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="d7918-113">Následující příklad je stejný jako ten výše, s výjimkou, že je strom XML načten do <xref:System.Xml.Linq.XDocument> namísto <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d7918-113">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="d7918-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d7918-114">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="d7918-115">Všimněte si, že stejný dotaz vrátil jeden `Root` uzel místo tří podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="d7918-115">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="d7918-116">Jedním z přístupů k tomu, abyste se s ním mohli pracovat, je použít <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před přístupem k metodám OS následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d7918-116">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="d7918-117">Tento dotaz teď funguje stejným způsobem jako dotaz na stromové struktuře, ve které se nachází root <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="d7918-117">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="d7918-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d7918-118">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  