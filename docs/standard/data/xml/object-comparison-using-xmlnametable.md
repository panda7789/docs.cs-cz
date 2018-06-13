---
title: Objekt porovnání pomocí XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09f717cb4c09c1e35b9472b7b549f1d3edf0dd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569275"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="b071b-102">Objekt porovnání pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="b071b-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="b071b-103">**XmlDocuments**, při vytváření, máte název tabulky vytvořené speciálně pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="b071b-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="b071b-104">Pokud načten do dokumentu nebo se vytvářejí nové elementy nebo atributy, názvy elementu a atributu jsou vloženy do **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="b071b-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="b071b-105">Můžete taky vytvořit **třídou XMLDocument nastavenou na** použití stávající **tabulky názvů** z jiného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b071b-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="b071b-106">Když **XmlDocuments** jsou vytvořeny pomocí konstruktor, který přebírá **XmlNameTable** parametr dokument má přístup k uzlu názvy, obory názvů a předpony, které jsou již uloženy v  **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="b071b-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="b071b-107">Bez ohledu na to, jak načíst název tabulky s názvy, jakmile se názvy jsou uložené v tabulce, názvy lze porovnat rychle pomocí objektu porovnání místo porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="b071b-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="b071b-108">Řetězce lze také přidat název tabulky pomocí <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="b071b-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="b071b-109">Následující příklad kódu ukazuje název tabulky vytváří a řetězec **MyString** přidávané do tabulky.</span><span class="sxs-lookup"><span data-stu-id="b071b-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="b071b-110">Potom **třídou XMLDocument nastavenou na** je vytvořený pomocí této tabulky a názvy elementu a atributu v **Myfile.xml** jsou přidány do existující název tabulky.</span><span class="sxs-lookup"><span data-stu-id="b071b-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="b071b-111">Následující příklad kódu ukazuje vytvoření dokumentu, dva nové prvky, který se přidává do dokumentu, který je také přidá do dokumentu název tabulky a porovnání objektu na názvy.</span><span class="sxs-lookup"><span data-stu-id="b071b-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="b071b-112">Výše uvedené scénáře předávají mezi dva dokumenty název tabulky je typické, když stejného typu dokumentu, jsou zpracovávány opakovaně, jako jsou dokumenty pořadí v lokalitě elektronické obchodování, která vyhovují schématu XML definition language (XSD) schéma nebo dokument typ definice (DTD) a stejné řetězce se opakují.</span><span class="sxs-lookup"><span data-stu-id="b071b-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="b071b-113">Pomocí stejné název tabulky dává zlepšení výkonu, jako stejným názvem elementu dochází v více dokumentů.</span><span class="sxs-lookup"><span data-stu-id="b071b-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b071b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b071b-114">See Also</span></span>  
 [<span data-ttu-id="b071b-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b071b-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
