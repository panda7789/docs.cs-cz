---
title: Načtení seřazených uzlů podle indexu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 8ff02a81ab579cc0041074990a76166fcafe6eb5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288716"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="5975f-102">Načtení seřazených uzlů podle indexu</span><span class="sxs-lookup"><span data-stu-id="5975f-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="5975f-103">Konsorcium World Wide Web (W3C) XML model DOM (Document Object Model) (DOM) také popisuje seznam uzlů., který má schopnost zpracovávat uspořádaný seznam uzlů, na rozdíl od neuspořádané sady, která je zpracována **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="5975f-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="5975f-104">Seznam uzlů. v Microsoft .NET Framework se nazývá **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="5975f-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="5975f-105">Metody a vlastnosti, které vracejí **XmlNodeList** , jsou:</span><span class="sxs-lookup"><span data-stu-id="5975f-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="5975f-106">XmlNode. ChildNodes</span><span class="sxs-lookup"><span data-stu-id="5975f-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="5975f-107">XmlDocument. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="5975f-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="5975f-108">XmlElement. GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="5975f-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="5975f-109">XmlNode. SelectNodes</span><span class="sxs-lookup"><span data-stu-id="5975f-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="5975f-110">**XmlNodeList** má vlastnost **Count** , kterou lze použít k zápisu smyček pro iteraci v uzlech **XmlNodeList**, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="5975f-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
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
  
 <span data-ttu-id="5975f-111">Kromě vlastnosti **Count** je k dispozici metoda **GetEnumerator** , která pro `foreach` kolekci uzlů v **XmlNodeList**poskytuje iteraci stylu.</span><span class="sxs-lookup"><span data-stu-id="5975f-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="5975f-112">Následující příklad kódu ukazuje použití `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="5975f-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="5975f-113">Další informace o metodách a vlastnostech dostupných v **XmlNodeList**naleznete v tématu <xref:System.Xml.XmlNodeList> .</span><span class="sxs-lookup"><span data-stu-id="5975f-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5975f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5975f-114">See also</span></span>

- [<span data-ttu-id="5975f-115">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5975f-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
