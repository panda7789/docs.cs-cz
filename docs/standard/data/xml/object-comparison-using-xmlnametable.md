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
# <a name="object-comparison-using-xmlnametable"></a>Porovnání objektů pomocí XmlNameTable
**XmlDocuments**, při vytvoření, máte název tabulky vytvořené speciálně pro tento dokument. Při načtení do dokumentu XML nebo nové elementy nebo atributy vytvořené, názvy atributů a element jsou vloženy do **XmlNameTable**. Můžete taky vytvořit **XmlDocument** použití stávající **tabulky názvů** z jiného dokumentu. Při **XmlDocuments** jsou vytvořeny pomocí konstruktoru, který přebírá **XmlNameTable** parametr, dokument má přístup k uzlu názvy, obory názvů a předpony, které už jsou uložené ve  **XmlNameTable**. Bez ohledu na to, jak načíst název tabulky s názvy, jakmile se názvy jsou uložené v tabulce, názvy mohou být porovnány rychle pomocí objektu porovnání namísto porovnání řetězců. Řetězce můžete také přidat pomocí názvu tabulky <xref:System.Xml.NameTable.Add%2A>. Následující příklad kódu ukazuje řetězec a název tabulky vytváří **MyString** přidávají do tabulky. Potom **třídou XMLDocument nastavenou na** je vytvořený pomocí tabulky a názvy prvků a atributů v **Myfile.xml** jsou přidány do existující název tabulky.  
  
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
  
 Následující příklad kódu ukazuje vytvoření dokumentu, dvě nové prvky, které se přidávají do dokumentu také přidá název tabulky dokumentů a porovnání objektu na názvy.  
  
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
  
 Název tabulky předané mezi dvěma dokumenty výše popsaném scénáři je obvyklá, když stejného typu dokumentu je zpracovávána opakovaně, jako je například pořadí dokumentů na webu elektronického obchodování, které odpovídají schématu XML definice jazyk (XSD) schématu nebo dokumentu typ definice (DTD) a stejné řetězce se opakují. Tabulka se stejným názvem pomocí poskytuje vylepšení výkonu, jako stejným názvem elementu dochází ve více dokumentů.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
