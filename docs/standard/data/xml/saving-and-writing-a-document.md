---
title: Ukládání a zápis dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 0af160b720b9eddd9e72689c920316bffdc6d21e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710216"
---
# <a name="saving-and-writing-a-document"></a>Ukládání a zápis dokumentu
Když načtete a uložíte <xref:System.Xml.XmlDocument>, uložený dokument se může lišit od originálu následujícími způsoby:  
  
- Pokud je vlastnost <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> nastavena na `true` před voláním metody <xref:System.Xml.XmlDocument.Save%2A>, prázdné místo v dokumentu zůstane ve výstupu. Pokud je tato vlastnost `false`, <xref:System.Xml.XmlDocument> automaticky odsadí výstup.  
  
- Všechny prázdné znaky mezi atributy jsou zmenšeny na jeden znak mezery.  
  
- Je změněno prázdné místo mezi prvky. Významné prázdné znaky jsou zachovány a nevýznamné prázdné znaky nejsou. Ale když se dokument uloží, použije se ve výchozím nastavení <xref:System.Xml.XmlTextWriter> režim **odsazení** , aby se výstup vytiskl, takže se bude čitelnější.  
  
- Znak citace použitý kolem hodnot atributů se ve výchozím nastavení změní na dvojité uvozovky. Vlastnost <xref:System.Xml.XmlTextReader.QuoteChar%2A> v <xref:System.Xml.XmlTextWriter> můžete použít k nastavení znaku uvozovky na dvojité uvozovky nebo jednoduché uvozovky.  
  
- Ve výchozím nastavení jsou rozbalené číselné znakové entity, jako je `{`.  
  
- Značka pořadí bajtů, která se nachází ve vstupním dokumentu, se nezachová. UCS-2 je uložen jako UTF-8, pokud explicitně nevytvoříte deklaraci XML, která určuje jiné kódování.  
  
- Pokud chcete <xref:System.Xml.XmlDocument> zapsat do souboru nebo datového proudu, vypsaný výstup je stejný jako obsah dokumentu. To znamená, že <xref:System.Xml.XmlDeclaration> je zapsána pouze v případě, že je obsažena v dokumentu a kódování použité při vypisování dokumentu je stejné kódování, které je zadáno v uzlu deklarace.  
  
## <a name="writing-an-xmldeclaration"></a>Zápis XmlDeclaration  
 <xref:System.Xml.XmlDocument> a <xref:System.Xml.XmlDeclaration> členové <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>a <xref:System.Xml.XmlNode.WriteTo%2A>, kromě <xref:System.Xml.XmlDocument>ch metod <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A>, vytvoří deklaraci XML.  
  
 Pro <xref:System.Xml.XmlDocument> vlastností <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>a metod <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>a <xref:System.Xml.XmlDocument.WriteContentTo%2A> se kódování zapsané v deklaraci XML povede z uzlu <xref:System.Xml.XmlDeclaration>. Pokud uzel není <xref:System.Xml.XmlDeclaration>, <xref:System.Xml.XmlDeclaration> nebude zapsán. Pokud není v uzlu <xref:System.Xml.XmlDeclaration> žádné kódování, kódování není zapsáno v deklaraci XML.  
  
 Metody <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> vždy vypisují <xref:System.Xml.XmlDeclaration>. Tyto metody přebírají kódování od zapisovače, do kterého se zapisuje. To znamená, že hodnota kódování u zapisovače Přepisuje kódování v dokumentu a <xref:System.Xml.XmlDeclaration>. Například následující kód nepíše kódování v deklaraci XML, které se nachází ve výstupním souboru `out.xml`.  
  
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
  
 Pro metodu <xref:System.Xml.XmlDocument.Save%2A> se deklarace XML zapisuje pomocí metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> ve třídě <xref:System.Xml.XmlWriter>. Proto přepsání metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> mění způsob, jakým je zapsán začátek dokumentu.  
  
 V případě <xref:System.Xml.XmlDeclaration>ch členů <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>a <xref:System.Xml.XmlNode.InnerXml%2A>, pokud vlastnost <xref:System.Xml.XmlDeclaration.Encoding%2A> není nastavena, nezapisuje se žádné kódování. Jinak kódování zapsané v deklaraci XML je stejné jako kódování nalezené ve vlastnosti <xref:System.Xml.XmlDeclaration.Encoding%2A>.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zápis obsahu dokumentu pomocí vlastnosti OuterXml  
 Vlastnost <xref:System.Xml.XmlNode.OuterXml%2A> je rozšířením Microsoft pro standardy XML model DOM (Document Object Model) (DOM) konsorcium World Wide Web (W3C). Vlastnost <xref:System.Xml.XmlNode.OuterXml%2A> slouží k získání značky celého dokumentu XML, nebo pouze označení jednoho uzlu a jeho podřízených uzlů. <xref:System.Xml.XmlNode.OuterXml%2A> vrátí značku reprezentující daný uzel a všechny jeho podřízené uzly.  
  
 Následující ukázka kódu ukazuje, jak uložit dokument jako celek jako řetězec.  
  
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
  
 Následující ukázka kódu ukazuje, jak uložit pouze element dokumentu.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Naopak můžete použít vlastnost <xref:System.Xml.XmlNode.InnerText%2A>, pokud chcete obsah podřízených uzlů.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
