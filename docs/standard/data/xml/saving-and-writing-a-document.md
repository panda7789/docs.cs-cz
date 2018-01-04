---
title: "Ukládání a zápis dokumentu"
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
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2138b9c47c6e41cd94e775eaed005d8a6fd976c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-writing-a-document"></a>Ukládání a zápis dokumentu
Při spouštění a uložit <xref:System.Xml.XmlDocument>, uložený dokument se můžou lišit od původního následujícími způsoby:  
  
-   Pokud <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> je nastavena na `true` před <xref:System.Xml.XmlDocument.Save%2A> metoda je volána, prázdné místo v dokumentu je zachována ve výstupu; pokud je tato vlastnost `false`, <xref:System.Xml.XmlDocument> automaticky odsazení výstup.  
  
-   Všechny mezer mezi atributy sníží jeden mezerou.  
  
-   Mezer mezi elementy se změní. Uchování významné prázdné znaky a není zanedbatelný prázdné znaky. Při ukládání dokumentu se bude používat, ale <xref:System.Xml.XmlTextWriter> **Indenting** režimu ve výchozím nastavení přehledně vytisknout výstup, aby byl čitelnější.  
  
-   Uvozovky používá kolem hodnoty atributu se změní na dvojitých uvozovek ve výchozím nastavení. Můžete použít <xref:System.Xml.XmlTextReader.QuoteChar%2A> vlastnost <xref:System.Xml.XmlTextWriter> nastavit uvozovky dvojité uvozovky nebo jednoduchých uvozovkách.  
  
-   Ve výchozím nastavení, jako například entity číselné znaků `{` rozbaleny.  
  
-   Značky pořadí bajtů nalezen v dokumentu vstupní není zachován. UCS-2 je uložena jako UTF-8, pokud explicitně vytvořit deklaraci XML, který určuje jinou kódování.  
  
-   Pokud chcete zapsat <xref:System.Xml.XmlDocument> do souboru nebo datový proud, zapsána výstup je stejný jako obsah dokumentu. To znamená <xref:System.Xml.XmlDeclaration> je napsána pouze pokud je obsažena v dokumentu a kódování použité při zápisu se dokumentu je stejný kódování uveden v uzlu deklarace.  
  
## <a name="writing-an-xmldeclaration"></a>Zápis XmlDeclaration  
 <xref:System.Xml.XmlDocument> a <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, a <xref:System.Xml.XmlNode.WriteTo%2A>, kromě <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A>, vytvořit deklaraci XML.  
  
 Pro <xref:System.Xml.XmlDocument> vlastnosti <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>a <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, a <xref:System.Xml.XmlDocument.WriteContentTo%2A> metody, kódování napsána v deklaraci XML je převzat ze <xref:System.Xml.XmlDeclaration> uzlu. Pokud neexistuje žádné <xref:System.Xml.XmlDeclaration> uzlu <xref:System.Xml.XmlDeclaration> není zapsaná. Pokud je v bez kódování <xref:System.Xml.XmlDeclaration> uzlu kódování není napsána v deklaraci XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody vždycky zapsat <xref:System.Xml.XmlDeclaration>. Tyto metody přijímají kódování z zapisovač, který zapisuje do. To znamená, kódování hodnota zapisovače přepsání kódování na dokument a na <xref:System.Xml.XmlDeclaration>. Například následující kód nelze zapsat kódování v deklaraci XML nalezen ve výstupním souboru `out.xml`.  
  
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
  
 Pro <xref:System.Xml.XmlDocument.Save%2A> metody deklarace XML je zapsána pomocí <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda v <xref:System.Xml.XmlWriter> – třída. Proto přepsal <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda mění, jak je zapsán začátek dokumentu.  
  
 Pro <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, a <xref:System.Xml.XmlNode.InnerXml%2A>, pokud <xref:System.Xml.XmlDeclaration.Encoding%2A> není nastavena vlastnost, bez kódování se zapíše. Jinak, kódování napsána v deklaraci XML je stejný jako kódování v nalezen <xref:System.Xml.XmlDeclaration.Encoding%2A> vlastnost.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Obsah dokumentu zápis pomocí vlastnosti OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost je rozšíření Microsoft standardům World Wide Web Consortium (W3C) XML modelu DOM (Document Object). <xref:System.Xml.XmlNode.OuterXml%2A> Vlastnost se používá k získání kódu celý dokument XML nebo kód jeden uzel a jeho podřízené uzly. <xref:System.Xml.XmlNode.OuterXml%2A>vrátí kód, který představuje daný uzel a všechny jeho podřízené uzly.  
  
 Následující příklad kódu ukazuje, jak k uložení dokumentu v celé jeho šíři jako řetězec.  
  
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
  
 Následující příklad kódu ukazuje, jak uložit jenom element dokumentu.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Naproti tomu můžete použít <xref:System.Xml.XmlNode.InnerText%2A> vlastnost, pokud chcete, aby obsah podřízené uzly.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
