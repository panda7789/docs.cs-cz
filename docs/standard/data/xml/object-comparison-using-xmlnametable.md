---
title: "Objekt porovnání pomocí XmlNameTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a>Objekt porovnání pomocí XmlNameTable
**XmlDocuments**, při vytváření, máte název tabulky vytvořené speciálně pro tento dokument. Pokud načten do dokumentu nebo se vytvářejí nové elementy nebo atributy, názvy elementu a atributu jsou vloženy do **XmlNameTable**. Můžete taky vytvořit **třídou XMLDocument nastavenou na** použití stávající **tabulky názvů** z jiného dokumentu. Když **XmlDocuments** jsou vytvořeny pomocí konstruktor, který přebírá **XmlNameTable** parametr dokument má přístup k uzlu názvy, obory názvů a předpony, které jsou již uloženy v  **XmlNameTable**. Bez ohledu na to, jak načíst název tabulky s názvy, jakmile se názvy jsou uložené v tabulce, názvy lze porovnat rychle pomocí objektu porovnání místo porovnání řetězců. Řetězce lze také přidat název tabulky pomocí <xref:System.Xml.NameTable.Add%2A>. Následující příklad kódu ukazuje název tabulky vytváří a řetězec **MyString** přidávané do tabulky. Potom **třídou XMLDocument nastavenou na** je vytvořený pomocí této tabulky a názvy elementu a atributu v **Myfile.xml** jsou přidány do existující název tabulky.  
  
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
  
 Následující příklad kódu ukazuje vytvoření dokumentu, dva nové prvky, který se přidává do dokumentu, který je také přidá do dokumentu název tabulky a porovnání objektu na názvy.  
  
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
  
 Výše uvedené scénáře předávají mezi dva dokumenty název tabulky je typické, když stejného typu dokumentu, jsou zpracovávány opakovaně, jako jsou dokumenty pořadí v lokalitě elektronické obchodování, která vyhovují schématu XML definition language (XSD) schéma nebo dokument typ definice (DTD) a stejné řetězce se opakují. Pomocí stejné název tabulky dává zlepšení výkonu, jako stejným názvem elementu dochází v více dokumentů.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
