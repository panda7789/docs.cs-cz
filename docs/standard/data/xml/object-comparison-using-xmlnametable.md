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
# <a name="object-comparison-using-xmlnametable"></a>Porovnání objektů pomocí XmlNameTable
V **případě, že**jsou vytvořeny, mají vytvořenou tabulku názvů specificky pro tento dokument. Když je do dokumentu načten kód XML, nebo jsou vytvořeny nové prvky nebo atributy, názvy atributů a elementů jsou vloženy do **XmlNameTable**. Můžete také vytvořit **XmlDocument** pomocí existující **NameTable** z jiného dokumentu. Když jsou vytvořeny **XmlDocument** pomocí konstruktoru, který přebírá parametr **XmlNameTable** , dokument má přístup k názvům uzlů, oborům názvů a předponám, které jsou již uloženy v **XmlNameTable**. Bez ohledu na to, jak je tabulka názvů načtena s názvy, jakmile jsou názvy uloženy v tabulce, lze názvy porovnávat rychle pomocí porovnání objektů namísto porovnání řetězců. Řetězce lze do tabulky názvů přidat také pomocí <xref:System.Xml.NameTable.Add%2A>. Následující ukázka kódu ukazuje vytvoření tabulky názvů a přidání řetězcové sady **MyString** do tabulky. Poté je vytvořen kód **XmlDocument** pomocí této tabulky a názvy elementů a atributů v **souboru MyFile. XML** jsou přidány do existující tabulky názvů.  
  
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
  
 Následující příklad kódu ukazuje vytvoření dokumentu, dva nové prvky, které jsou přidány do dokumentu, který je také přidá do tabulky názvů dokumentů, a porovnání objektů s názvy.  
  
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
  
 Výše uvedený scénář tabulky názvů předaných mezi dvěma dokumenty je typický při opakovaném zpracování stejného typu dokumentu, jako je například objednávka dokumentů na webu elektronického obchodování, který je v souladu se schématem jazyka XML (XSD) nebo typem dokumentu. definice (DTD) a stejné řetězce se opakují. Použití stejné tabulky názvů přináší vylepšení výkonu, protože stejný název elementu se vyskytuje ve více dokumentech.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
