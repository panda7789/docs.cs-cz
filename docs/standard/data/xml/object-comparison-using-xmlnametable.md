---
title: Porovnání objektů pomocí XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 814f5434dd0473b3b1dd613a2eba14a828c464d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936705"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="1ccdc-102">Porovnání objektů pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="1ccdc-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="1ccdc-103">**XmlDocuments**, při vytvoření, máte název tabulky vytvořené speciálně pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="1ccdc-104">Při načtení do dokumentu XML nebo nové elementy nebo atributy vytvořené, názvy atributů a element jsou vloženy do **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="1ccdc-105">Můžete taky vytvořit **XmlDocument** použití stávající **tabulky názvů** z jiného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="1ccdc-106">Při **XmlDocuments** jsou vytvořeny pomocí konstruktoru, který přebírá **XmlNameTable** parametr, dokument má přístup k uzlu názvy, obory názvů a předpony, které už jsou uložené ve  **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="1ccdc-107">Bez ohledu na to, jak načíst název tabulky s názvy, jakmile se názvy jsou uložené v tabulce, názvy mohou být porovnány rychle pomocí objektu porovnání namísto porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="1ccdc-108">Řetězce můžete také přidat pomocí názvu tabulky <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="1ccdc-109">Následující příklad kódu ukazuje řetězec a název tabulky vytváří **MyString** přidávají do tabulky.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="1ccdc-110">Potom **třídou XMLDocument nastavenou na** je vytvořený pomocí tabulky a názvy prvků a atributů v **Myfile.xml** jsou přidány do existující název tabulky.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="1ccdc-111">Následující příklad kódu ukazuje vytvoření dokumentu, dvě nové prvky, které se přidávají do dokumentu také přidá název tabulky dokumentů a porovnání objektu na názvy.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="1ccdc-112">Název tabulky předané mezi dvěma dokumenty výše popsaném scénáři je obvyklá, když stejného typu dokumentu je zpracovávána opakovaně, jako je například pořadí dokumentů na webu elektronického obchodování, které odpovídají schématu XML definice jazyk (XSD) schématu nebo dokumentu typ definice (DTD) a stejné řetězce se opakují.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="1ccdc-113">Tabulka se stejným názvem pomocí poskytuje vylepšení výkonu, jako stejným názvem elementu dochází ve více dokumentů.</span><span class="sxs-lookup"><span data-stu-id="1ccdc-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ccdc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ccdc-114">See also</span></span>

- [<span data-ttu-id="1ccdc-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="1ccdc-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
