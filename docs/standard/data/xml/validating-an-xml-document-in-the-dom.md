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
ms.openlocfilehash: b77d26a79796a9de87c07e366929cb516169907b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM
<xref:System.Xml.XmlDocument> Třída nelze ověřit kód XML v objektu modelu dokumentu (DOM) proti schématu XML definice jazyka (XSD) schématu nebo s dokumentem definice typu (DTD) ve výchozím nastavení; XML se ověří pouze se ve správném formátu.  
  
 Ověření XML v modelu DOM, můžete ověřit XML, jako je načten do modelu DOM předáním schéma ověřování <xref:System.Xml.XmlReader> k <xref:System.Xml.XmlDocument.Load%2A> metodu <xref:System.Xml.XmlDocument> třídy nebo ověřit dříve neověřený dokumentu XML v modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Dokument XML, jako je ověřování je načten do modelu DOM  
 <xref:System.Xml.XmlDocument> Třída ověří XML data, jako je načten do modelu DOM při ověření <xref:System.Xml.XmlReader> předaný <xref:System.Xml.XmlDocument.Load%2A> metodu <xref:System.Xml.XmlDocument> třídy.  
  
 Po úspěšném ověření se použijí výchozí hodnoty schématu, textové hodnoty jsou převedeny na atomic hodnoty podle potřeby a informací o typu souvisí s položkami ověřené informace. V důsledku toho zadaných dat XML nahradí dříve netypové data XML.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Vytváření XML schéma ověřování XmlReader  
 Chcete-li vytvořit XML schéma ověřování <xref:System.Xml.XmlReader>, postupujte podle těchto kroků.  
  
1.  Vytvořit nový <xref:System.Xml.XmlReaderSettings> instance.  
  
2.  Přidat schéma XML <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> instance.  
  
3.  Zadejte `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  Volitelně zadejte <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> pro zpracování chyby ověřování schématu a upozornění při ověřování došlo k.  
  
5.  Nakonec předat <xref:System.Xml.XmlReaderSettings> do objektu <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třída společně s dokument XML, vytváření, schématu ověření <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Příklad  
 V příkladu kódu, který následuje, schématu ověření <xref:System.Xml.XmlReader> ověří data XML, který je načten do modelu DOM. Neplatné změny provedené v dokumentu XML a dokumentu je pak znovu ověřeny, příčinou chyby ověřování schématu. Nakonec některé z chyb po opravě a pak je součástí v dokumentu XML částečně ověřit.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 V příkladu trvá `contosoBooks.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Tento příklad také trvá `contosoBooks.xsd` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Vezměte v úvahu následující při ověřování dat XML, jako je načten do modelu DOM.  
  
-   V předchozím příkladu <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je volána, když se zjistil neplatný typ. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> není nastaven na ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána při <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud žádný typ elementu nebo atributu neodpovídá odpovídající typ zadaný v ověřování schématu.  
  
-   Když je dokument XML načten do <xref:System.Xml.XmlDocument> objekt s přidružené schéma, která definuje výchozí hodnoty <xref:System.Xml.XmlDocument> zpracovává tato výchozí nastavení, jako kdyby byly zobrazeny v dokumentu XML. To znamená, že <xref:System.Xml.XmlReader.IsEmptyElement%2A> vlastnost vždy vrátí hodnotu `false` pro element, který byl uvedena ze schématu. I když v dokumentu XML byla zapsána jako prázdný element.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM  
 <xref:System.Xml.XmlDocument.Validate%2A> Metodu <xref:System.Xml.XmlDocument> třída ověří data XML, který je načten do modelu DOM proti schémata v <xref:System.Xml.XmlDocument> objektu <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost. Po úspěšném ověření se použijí výchozí hodnoty schématu, textové hodnoty jsou převedeny na atomic hodnoty podle potřeby a informací o typu souvisí s položkami ověřené informace. V důsledku toho zadaných dat XML nahradí dříve netypové data XML.  
  
 Následující příklad je podobné jako v příkladu v "Ověřování XML dokumentu jako jeho je načíst do modelu DOM" výše. V tomto příkladu není v dokumentu XML ověřit, protože je načíst do modelu DOM, ale spíše je ověřen po byl načten do modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XmlDocument.Validate%2A> Metoda ověří proti schémat XML obsažených v dokumentu XML <xref:System.Xml.XmlDocument.Schemas%2A> vlastnost <xref:System.Xml.XmlDocument>. Neplatný pak úprav dokumentu XML a dokumentu je pak znovu ověřeny, příčinou chyby ověřování schématu. Nakonec některé z chyb po opravě a pak je součástí v dokumentu XML částečně ověřit.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Příklad přijímá jako vstup `contosoBooks.xml` a `contosoBooks.xsd` soubory uvedené v "Ověřování XML dokumentu jako jeho je načíst do DOM" výše.  
  
## <a name="handling-validation-errors-and-warnings"></a>Zpracování chyb při ověřování a upozornění  
 Při ověřování dat XML načítání do modelu DOM. vznikly chyby ověřování schématu XML Jsou oznámení o všechny chyby ověřování schématu zjištěné při ověřování dat XML, jako jsou načítány, nebo když ověřování dříve neověřený dokumentu XML.  
  
 Chyby ověření jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler>. Pokud <xref:System.Xml.Schema.ValidationEventHandler> byl přiřazen <xref:System.Xml.XmlReaderSettings> instance nebo předaný <xref:System.Xml.XmlDocument.Validate%2A> metodu <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.Schema.ValidationEventHandler> bude zpracovávat chyby ověřování schématu; jinak <xref:System.Xml.Schema.XmlSchemaValidationException> se vyvolá, když se ověřování schématu došlo k chybě.  
  
> [!NOTE]
>  Načtení dat XML do modelu DOM navzdory chyby ověřování schématu Pokud vaše <xref:System.Xml.Schema.ValidationEventHandler> vyvolá výjimku proces zastavíte.  
>   
>  Upozornění na ověření schématu nejsou uvedeny, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> příznak je určena k <xref:System.Xml.XmlReaderSettings> objektu.  
  
 Příklady ilustrující <xref:System.Xml.Schema.ValidationEventHandler>, najdete v části "Ověřování XML dokumentu jako ho je načten do DOM" a "Ověřování XML dokumentu v modelu DOM" výše.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.ValidationEventHandler>  
 <xref:System.Xml.XmlReaderSettings>  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
