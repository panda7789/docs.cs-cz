---
title: Načtení seřazených uzlů podle indexu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 515edf26df6190d2bf4906f3de2d019b1a4175fb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276260"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="bb1dc-102">Načtení seřazených uzlů podle indexu</span><span class="sxs-lookup"><span data-stu-id="bb1dc-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="bb1dc-103">World Wide Web Consortium (W3C) XML Document Object Model (DOM) také popisuje seznamu, který má schopnost zpracovávat uspořádaný seznam uzlů, na rozdíl od neuspořádanou sadu zpracována **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="bb1dc-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="bb1dc-104">Je volána seznamu v rozhraní Microsoft .NET Framework **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="bb1dc-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="bb1dc-105">Metody a vlastnosti, které vracejí **XmlNodeList** jsou:</span><span class="sxs-lookup"><span data-stu-id="bb1dc-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
-   <span data-ttu-id="bb1dc-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="bb1dc-106">XmlNode.ChildNodes</span></span>  
  
-   <span data-ttu-id="bb1dc-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="bb1dc-107">XmlDocument.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="bb1dc-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="bb1dc-108">XmlElement.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="bb1dc-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="bb1dc-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="bb1dc-110">**XmlNodeList** má **počet** vlastnost, která umožňuje psát smyčky k iteraci přes uzly v **XmlNodeList**, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="bb1dc-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 <span data-ttu-id="bb1dc-111">Kromě **počet** vlastnost, je **GetEnumerator** metodu, která poskytuje, `foreach` stylu iterace přes kolekce uzlů v **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="bb1dc-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="bb1dc-112">Následující příklad kódu ukazuje použití `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="bb1dc-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="bb1dc-113">Další informace o metody a vlastnosti, které jsou k dispozici na **XmlNodeList**, naleznete v tématu <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="bb1dc-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1dc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb1dc-114">See also</span></span>

- [<span data-ttu-id="bb1dc-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="bb1dc-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
