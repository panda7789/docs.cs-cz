---
title: Ukládání a zápis dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83aad5d45dda1784069839662486f7dbcc307542
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027027"
---
# <a name="saving-and-writing-a-document"></a>Ukládání a zápis dokumentu
Při načtení a uložení <xref:System.Xml.XmlDocument>, uložený dokument může lišit od původních následujícími způsoby:  
  
- Pokud <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> je nastavena na `true` před <xref:System.Xml.XmlDocument.Save%2A> metoda je volána, prázdné znaky v dokumentu je zachována ve výstupu; pokud je tato vlastnost `false`, <xref:System.Xml.XmlDocument> Automatické odsazení výstupu.  
  
- Všechny prázdné znaky mezi atributy se zkrátilo na jediné místo znak.  
  
- Prázdné znaky mezi elementy se změní. Zachování významných mezer a nevýznamné prázdný znak není. Ale když je dokument uložen, použije <xref:System.Xml.XmlTextWriter> **Indenting** režimu ve výchozím nastavení elegantně vytisknout výstup, aby byl lépe čitelný.  
  
- Uvozovky kolem hodnot atributů použít se změní na dvojitými uvozovkami. ve výchozím nastavení. Můžete použít <xref:System.Xml.XmlTextReader.QuoteChar%2A> vlastnost <xref:System.Xml.XmlTextWriter> nastavit znak pro uvození dvojité uvozovky nebo jednoduchá uvozovka.  
  
- Ve výchozím nastavení, jako je číselný znak entity `{` rozbaleny.  
  
- Nezachová se značkou pořadí bajtů nalezen ve vstupním dokumentu. UCS-2 je uložen jako UTF-8, dokud explicitně nevytvoříte deklarace XML, který určuje jiné kódování.  
  
- Pokud chcete vypsat <xref:System.Xml.XmlDocument> do souboru nebo datového proudu zapsat výstup je stejný jako obsah dokumentu. To znamená <xref:System.Xml.XmlDeclaration> je zapsán pouze pokud je obsažena v dokumentu a kódování použité při zápisu dokument je stejný kódování podle uzlu deklarací.  
  
## <a name="writing-an-xmldeclaration"></a>Zápis XmlDeclaration  
 <xref:System.Xml.XmlDocument> a <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, a <xref:System.Xml.XmlNode.WriteTo%2A>, kromě <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A>, vytvořit deklaraci XML.  
  
 Pro <xref:System.Xml.XmlDocument> vlastnosti <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>a <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, a <xref:System.Xml.XmlDocument.WriteContentTo%2A> metody, kódování, které je zapsané v deklaraci XML je převzata z <xref:System.Xml.XmlDeclaration> uzlu. Pokud není žádný <xref:System.Xml.XmlDeclaration> uzlu <xref:System.Xml.XmlDeclaration> není zapsán. Pokud není v žádné kódování <xref:System.Xml.XmlDeclaration> uzlu kódování není zapsán v deklaraci XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody vždy vypsat <xref:System.Xml.XmlDeclaration>. Tyto metody přijímají kódování z zapisovače, který zapisuje do. To znamená, přepíše hodnotu kódování zapisovače kódování v dokumentu a v <xref:System.Xml.XmlDeclaration>. Například následující kód nezapisuje kódování v deklaraci XML nalezen ve výstupním souboru `out.xml`.  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 Pro <xref:System.Xml.XmlDocument.Save%2A> metody deklarace XML je zapsán pomocí <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metodu <xref:System.Xml.XmlWriter> třídy. Přepsání proto, <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda mění, jak se zapíše začátek dokumentu.  
  
 Pro <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, a <xref:System.Xml.XmlNode.InnerXml%2A>, pokud <xref:System.Xml.XmlDeclaration.Encoding%2A> vlastnost není nastavená, bez kódování je zapsán. V opačném případě kódování napsaných v deklaraci XML je stejný jako kódování najdete v <xref:System.Xml.XmlDeclaration.Encoding%2A> vlastnost.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Vytváření obsahu dokumentu pomocí vlastnosti OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost je rozšířením společnosti Microsoft pro World Wide Web Consortium (W3C) XML Document Object Model (DOM) normami. <xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost se používá k získání značek celý dokument XML, nebo pouze značky, jeden uzel a jeho podřízené uzly. <xref:System.Xml.XmlNode.OuterXml%2A> vrátí kód představující daný uzel a všechny jeho podřízené uzly.  
  
 Následující příklad kódu ukazuje, jak uložit dokument v celém rozsahu jako řetězec.  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 Následující příklad kódu ukazuje, jak uložit pouze element dokumentu.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Naproti tomu můžete použít <xref:System.Xml.XmlNode.InnerText%2A> vlastnosti, pokud chcete obsah z podřízených uzlů.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
