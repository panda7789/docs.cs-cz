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
# <a name="ordered-node-retrieval-by-index"></a>Načtení seřazených uzlů podle indexu
Konsorcium World Wide Web (W3C) XML model DOM (Document Object Model) (DOM) také popisuje seznam uzlů., který má schopnost zpracovávat uspořádaný seznam uzlů, na rozdíl od neuspořádané sady, která je zpracována **XmlNamedNodeMap**. Seznam uzlů. v Microsoft .NET Framework se nazývá **XmlNodeList**. Metody a vlastnosti, které vracejí **XmlNodeList** , jsou:  
  
- XmlNode. ChildNodes  
  
- XmlDocument. GetElementsByTagName  
  
- XmlElement. GetElementsByTagName  
  
- XmlNode. SelectNodes  
  
 **XmlNodeList** má vlastnost **Count** , kterou lze použít k zápisu smyček pro iteraci v uzlech **XmlNodeList**, jak je znázorněno v následujícím příkladu kódu:  
  
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
  
 Kromě vlastnosti **Count** je k dispozici metoda **GetEnumerator** , která pro `foreach` kolekci uzlů v **XmlNodeList**poskytuje iteraci stylu. Následující příklad kódu ukazuje použití `foreach` příkazu.  
  
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
  
 Další informace o metodách a vlastnostech dostupných v **XmlNodeList**naleznete v tématu <xref:System.Xml.XmlNodeList> .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
