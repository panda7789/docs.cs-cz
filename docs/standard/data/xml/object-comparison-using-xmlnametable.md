---
title: Porovnání objektů pomocí XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 63278f1aa1fe47377d2dae322a9d12338bbe45dd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710528"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="8daa1-102">Porovnání objektů pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="8daa1-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="8daa1-103">V **případě, že**jsou vytvořeny, mají vytvořenou tabulku názvů specificky pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="8daa1-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="8daa1-104">Když je do dokumentu načten kód XML, nebo jsou vytvořeny nové prvky nebo atributy, názvy atributů a elementů jsou vloženy do **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="8daa1-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="8daa1-105">Můžete také vytvořit **XmlDocument** pomocí existující **NameTable** z jiného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8daa1-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="8daa1-106">Když jsou vytvořeny **XmlDocument** pomocí konstruktoru, který přebírá parametr **XmlNameTable** , dokument má přístup k názvům uzlů, oborům názvů a předponám, které jsou již uloženy v **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="8daa1-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="8daa1-107">Bez ohledu na to, jak je tabulka názvů načtena s názvy, jakmile jsou názvy uloženy v tabulce, lze názvy porovnávat rychle pomocí porovnání objektů namísto porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="8daa1-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="8daa1-108">Řetězce lze do tabulky názvů přidat také pomocí <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="8daa1-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="8daa1-109">Následující ukázka kódu ukazuje vytvoření tabulky názvů a přidání řetězcové sady **MyString** do tabulky.</span><span class="sxs-lookup"><span data-stu-id="8daa1-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="8daa1-110">Poté je vytvořen kód **XmlDocument** pomocí této tabulky a názvy elementů a atributů v **souboru MyFile. XML** jsou přidány do existující tabulky názvů.</span><span class="sxs-lookup"><span data-stu-id="8daa1-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="8daa1-111">Následující příklad kódu ukazuje vytvoření dokumentu, dva nové prvky, které jsou přidány do dokumentu, který je také přidá do tabulky názvů dokumentů, a porovnání objektů s názvy.</span><span class="sxs-lookup"><span data-stu-id="8daa1-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="8daa1-112">Výše uvedený scénář tabulky názvů předaných mezi dvěma dokumenty je typický při opakovaném zpracování stejného typu dokumentu, jako je například objednávka dokumentů na webu elektronického obchodování, který je v souladu se schématem XML Schema Definition Language (XSD) nebo definicí typu dokumentu (DTD) a se opakují stejné řetězce.</span><span class="sxs-lookup"><span data-stu-id="8daa1-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="8daa1-113">Použití stejné tabulky názvů přináší vylepšení výkonu, protože stejný název elementu se vyskytuje ve více dokumentech.</span><span class="sxs-lookup"><span data-stu-id="8daa1-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8daa1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8daa1-114">See also</span></span>

- [<span data-ttu-id="8daa1-115">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="8daa1-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
