---
title: Ukládání a zápis dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289041"
---
# <a name="saving-and-writing-a-document"></a>Ukládání a zápis dokumentu
Při načítání a ukládání se <xref:System.Xml.XmlDocument> může uložený dokument od originálu lišit následujícími způsoby:  
  
- Pokud je <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> vlastnost nastavena na hodnotu `true` před <xref:System.Xml.XmlDocument.Save%2A> voláním metody, prázdné místo v dokumentu zůstane ve výstupu. Pokud je tato vlastnost nastavena `false` , <xref:System.Xml.XmlDocument> automaticky odsadí výstup.  
  
- Všechny prázdné znaky mezi atributy jsou zmenšeny na jeden znak mezery.  
  
- Je změněno prázdné místo mezi prvky. Významné prázdné znaky jsou zachovány a nevýznamné prázdné znaky nejsou. Ale když se dokument uloží, použije se <xref:System.Xml.XmlTextWriter> ve výchozím nastavení režim **odsazení** k tomu, aby se výstup vytiskl, aby se čitelnější.  
  
- Znak citace použitý kolem hodnot atributů se ve výchozím nastavení změní na dvojité uvozovky. Pomocí <xref:System.Xml.XmlTextReader.QuoteChar%2A> vlastnosti zapnuto můžete <xref:System.Xml.XmlTextWriter> nastavit znak citace buď na dvojité uvozovky, nebo na jednoduché uvozovky.  
  
- Ve výchozím nastavení jsou rozšířeny číselné znakové entity jako `{` rozbalené.  
  
- Značka pořadí bajtů, která se nachází ve vstupním dokumentu, se nezachová. UCS-2 je uložen jako UTF-8, pokud explicitně nevytvoříte deklaraci XML, která určuje jiné kódování.  
  
- Pokud chcete zapisovat <xref:System.Xml.XmlDocument> do souboru nebo datového proudu, vypsaný výstup je stejný jako obsah dokumentu. To znamená, že <xref:System.Xml.XmlDeclaration> je zapsána pouze v případě, že je obsažena v dokumentu a kódování použité při vypisování dokumentu je stejné kódování, které je zadáno v uzlu deklarace.  
  
## <a name="writing-an-xmldeclaration"></a>Zápis XmlDeclaration  
 <xref:System.Xml.XmlDocument>A <xref:System.Xml.XmlDeclaration> členy a, <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> a <xref:System.Xml.XmlNode.WriteTo%2A> , kromě <xref:System.Xml.XmlDocument> metod <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteContentTo%2A> , vytvořte deklaraci XML.  
  
 Pro <xref:System.Xml.XmlDocument> vlastnosti <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDocument.InnerXml%2A> , a metody,, <xref:System.Xml.XmlDocument.Save%2A> a <xref:System.Xml.XmlDocument.WriteTo%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> je kódování zapsané v deklaraci XML získáno z <xref:System.Xml.XmlDeclaration> uzlu. Pokud není žádný <xref:System.Xml.XmlDeclaration> uzel, není <xref:System.Xml.XmlDeclaration> zapsán. Pokud v uzlu není žádné kódování <xref:System.Xml.XmlDeclaration> , kódování není zapsáno v deklaraci XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType>Metody a <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> vždy vypisují <xref:System.Xml.XmlDeclaration> . Tyto metody přebírají kódování od zapisovače, do kterého se zapisuje. To znamená, že hodnota kódování u zapisovače Přepisuje kódování v dokumentu a v <xref:System.Xml.XmlDeclaration> . Například následující kód nepíše kódování v deklaraci XML, které se nachází ve výstupním souboru `out.xml` .  
  
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
  
 V případě <xref:System.Xml.XmlDocument.Save%2A> metody je deklarace XML zapisována pomocí <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody ve <xref:System.Xml.XmlWriter> třídě. Proto přepsání <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody změní způsob, jakým je zapsán začátek dokumentu.  
  
 Pro <xref:System.Xml.XmlDeclaration> členy <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> a <xref:System.Xml.XmlNode.InnerXml%2A> , pokud <xref:System.Xml.XmlDeclaration.Encoding%2A> vlastnost není nastavena, není zapsáno kódování. Jinak kódování zapsané v deklaraci XML je stejné jako kódování nalezené ve <xref:System.Xml.XmlDeclaration.Encoding%2A> Vlastnosti.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zápis obsahu dokumentu pomocí vlastnosti OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A>Vlastnost je rozšířením společnosti Microsoft pro standardy XML konsorcium World Wide Web (W3C) model DOM (Document Object Model) (DOM). <xref:System.Xml.XmlNode.OuterXml%2A>Vlastnost slouží k získání značky celého dokumentu XML, nebo pouze označení jednoho uzlu a jeho podřízených uzlů. <xref:System.Xml.XmlNode.OuterXml%2A>Vrátí značku reprezentující daný uzel a všechny jeho podřízené uzly.  
  
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
  
 Naopak můžete použít <xref:System.Xml.XmlNode.InnerText%2A> vlastnost, pokud chcete obsah podřízených uzlů.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
