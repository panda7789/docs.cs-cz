---
title: Ověřování dokumentu XML v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0f5ae64eb1017570a56efab59a4bf1a66d5e02b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532672"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM
<xref:System.Xml.XmlDocument> Třídy nelze ověřit kód XML v objektu modelu dokumentu (DOM) proti schéma XML definice jazyk (XSD) schématu nebo dokumentu typ definice (DTD) ve výchozím nastavení; XML je jenom ověřit, být ve správném formátu.  
  
 Ověření XML v modelu DOM, můžete ověřit XML jako načtení do modelu DOM předáním schéma ověřování <xref:System.Xml.XmlReader> k <xref:System.Xml.XmlDocument.Load%2A> metodu <xref:System.Xml.XmlDocument> třídy nebo ověřit dřív neověřených dokument XML v modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Ověřování dokumentu XML jako jeho načtení do modelu DOM  
 <xref:System.Xml.XmlDocument> Třídy ověří XML data jako načtení do modelu DOM při ověřování <xref:System.Xml.XmlReader> je předán <xref:System.Xml.XmlDocument.Load%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 Po úspěšném ověření se použijí výchozí hodnoty schématu, textové hodnoty se převedou na Atomický hodnoty podle potřeby a informace o typu je přidružený k ověřených informačních položek. Typy dat XML v důsledku toho nahrazuje dříve netypový kód XML data.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Vytváření XML schéma ověřování XmlReader  
 Vytvoření XML schémat ověřování <xref:System.Xml.XmlReader>, postupujte podle těchto kroků.  
  
1.  Vytvořit nový <xref:System.Xml.XmlReaderSettings> instance.  
  
2.  Přidat schéma XML <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> instance.  
  
3.  Zadejte `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  Volitelně můžete zadat <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> pro zpracování chyby ověřování schématu a při ověřování došlo k upozornění.  
  
5.  Nakonec předat <xref:System.Xml.XmlReaderSettings> objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy společně s dokumentu XML, vytváří se schéma ověřování <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Příklad  
 V příkladu kódu, který následuje, schématu ověření <xref:System.Xml.XmlReader> ověří data XML načtení do modelu DOM. Neplatný úpravy probíhají v dokumentu XML a je dokument poté ověřit, což způsobí chyby ověřování schématu. Nakonec jeden z chyby opravit a pak je součástí dokumentu XML částečně ověřený.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 V příkladu přebírá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad využívá taky `contosoBooks.xsd` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Vezměte v úvahu následující při ověřování dat XML, jako je načten do modelu DOM.  
  
-   Ve výše uvedeném příkladu <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je volána pokaždé, když se zjistil se neplatný typ. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> není nastavená na ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána, když <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud libovolný typ atributu nebo elementu se neshoduje s odpovídající typ zadaný v ověřování schématu.  
  
-   Po načtení dokumentu XML do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, který definuje výchozí hodnoty <xref:System.Xml.XmlDocument> zpracuje tato výchozí nastavení, jako jsou uvedeny v dokumentu XML. To znamená, že <xref:System.Xml.XmlReader.IsEmptyElement%2A> vždy vrátí vlastnost `false` pro element, který byl převezme ve schématu. I v případě, že v dokumentu XML, byla zapsána jako prázdný prvek.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM  
 <xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třídy ověří data XML, který je načten v modelu DOM pomocí schémat v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost. Po úspěšném ověření se použijí výchozí hodnoty schématu, textové hodnoty se převedou na Atomický hodnoty podle potřeby a informace o typu je přidružený k ověřených informačních položek. Typy dat XML v důsledku toho nahrazuje dříve netypový kód XML data.  
  
 Následující příklad je podobné jako v příkladu v "Ověřování XML dokumentu jako to je načten do modelu DOM" výše. V tomto příkladu není ověřený dokumentu XML, jako je načteno do modelu DOM, ale místo toho se ověří po načtení do modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XmlDocument.Validate%2A> Metoda ověří proti schémat XML obsažených v dokumentu XML <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost <xref:System.Xml.XmlDocument>. Neplatný pak změn v dokumentu XML a je dokument poté ověřit, což způsobí chyby ověřování schématu. Nakonec jeden z chyby opravit a pak je součástí dokumentu XML částečně ověřený.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Příklad přijímá jako vstup `contosoBooks.xml` a `contosoBooks.xsd` soubory uvedené v "Ověřování XML dokumentu jako to je načten do modelu DOM" výše.  
  
## <a name="handling-validation-errors-and-warnings"></a>Zpracování chyby a upozornění ověření  
 Chyby ověřování schématu XML jsou hlášeny při ověřování dat XML načtení do modelu DOM. Se zobrazí oznámení o všechny chyby ověřování schématu při ověřování dat XML, jako jsou načítány, nebo při ověřování dřív neověřených dokumentu XML.  
  
 Chyby ověření jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler>. Pokud <xref:System.Xml.Schema.ValidationEventHandler> přiřadila se <xref:System.Xml.XmlReaderSettings> instance nebo předat <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.Schema.ValidationEventHandler> bude zpracovávat chyby ověřování schématu. v opačném <xref:System.Xml.Schema.XmlSchemaValidationException> se vyvolá, když se ověřování schématu došlo k chybě.  
  
> [!NOTE]
>  XML data se načtou do modelu DOM, bez ohledu na chyby ověřování schématu, pokud vaše <xref:System.Xml.Schema.ValidationEventHandler> vyvolává výjimku ukončit proces.  
>   
>  Upozornění při ověřování schématu nezobrazují, dokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> označen příznakem do <xref:System.Xml.XmlReaderSettings> objektu.  
  
 Příklady ilustrující <xref:System.Xml.Schema.ValidationEventHandler>, naleznete v tématu "Ověřování XML dokumentu jako to je načten do modelu DOM" a "Ověřování XML dokumentu v modelu DOM" výše.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.ValidationEventHandler>  
- <xref:System.Xml.XmlReaderSettings>  
- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
