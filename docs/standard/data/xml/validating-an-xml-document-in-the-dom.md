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
ms.openlocfilehash: b25bf81a17b14da558fb002b4740e31d6cda7a82
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040455"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

<xref:System.Xml.XmlDocument> Třída neověřuje XML v model DOM (Document Object Model) (DOM) proti schématu XSD (XML Schema Definition Language) nebo definici typu dokumentu (DTD) ve výchozím nastavení. XML je ověřeno pouze ve správném formátu.

Chcete-li ověřit XML v modelu DOM, můžete ověřit XML, jak je načteno do modelu DOM předáním schématu – ověření <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument.Load%2A> do metody <xref:System.Xml.XmlDocument> třídy, nebo ověření dříve neověřeného dokumentu XML v modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metoda třídy.<xref:System.Xml.XmlDocument>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Ověření dokumentu XML, jak je načteno do modelu DOM

Třída ověřuje data XML, když jsou načtena do modelu DOM při ověřování <xref:System.Xml.XmlReader> je předán <xref:System.Xml.XmlDocument.Load%2A> metodě <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XmlDocument>

Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Vytvoření schématu XML – ověření objektu XmlReader

Chcete-li vytvořit schéma XML – <xref:System.Xml.XmlReader>ověřování, postupujte podle těchto kroků.

1. Vytvořte novou <xref:System.Xml.XmlReaderSettings> instanci.

2. Přidejte schéma XML do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> instance.

3. `Schema` Zadejte<xref:System.Xml.XmlReaderSettings.ValidationType%2A>jako.

4. Volitelně můžete <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> zadat <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> a a zpracovat chyby ověřování schématu a upozornění zjištěná během ověřování.

5. Nakonec předejte <xref:System.Xml.XmlReaderSettings> objekt <xref:System.Xml.XmlReader.Create%2A> do metody <xref:System.Xml.XmlReader> třídy spolu s dokumentem XML a vytvořte ověřování <xref:System.Xml.XmlReader>schématu.

### <a name="example"></a>Příklad

V následujícím příkladu kódu ověřování <xref:System.Xml.XmlReader> schématu ověřuje XML data načtená do modelu DOM. V dokumentu XML jsou provedeny neplatné změny a potom se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Příklad přebírá `contosoBooks.xml` soubor jako vstup.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Příklad také přebírá `contosoBooks.xsd` soubor jako vstup.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Při ověřování dat XML při jejich načítání do modelu DOM Vezměte v úvahu následující skutečnosti.

- Ve výše uvedeném příkladu <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je volána při každém zjištění neplatného typu. Pokud není nastavena při ověřování <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána výjimka, když <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v rámci ověřování schématu. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>

- Při načtení dokumentu XML do <xref:System.Xml.XmlDocument> objektu s přidruženým schématem, které definuje výchozí hodnoty <xref:System.Xml.XmlDocument> , zpracovává tyto výchozí hodnoty, jako by se zobrazily v dokumentu XML. To znamená, že <xref:System.Xml.XmlReader.IsEmptyElement%2A> vlastnost vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ze schématu. I když v dokumentu XML, byl napsán jako prázdný prvek.

## <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

Metoda třídy ověřuje data XML načtená v modelu DOM <xref:System.Xml.XmlDocument> proti <xref:System.Xml.XmlDocument.Schemas%2A> schématům ve vlastnosti objektu. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Validate%2A> Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

Následující příklad je podobný příkladu v tématu "ověřování dokumentu XML při jeho načtení do modelu DOM" výše. V tomto příkladu není dokument XML ověřen, protože je načten do modelu DOM, ale je ověřen poté, co byl načten do modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy. Metoda ověří dokument XML proti schématům XML obsaženým <xref:System.Xml.XmlDocument.Schemas%2A> ve vlastnosti <xref:System.Xml.XmlDocument>. <xref:System.Xml.XmlDocument.Validate%2A> V dokumentu XML jsou následně provedeny neplatné změny a pak se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Příklad přijímá jako vstup `contosoBooks.xml` soubory a `contosoBooks.xsd` , na které se říká "ověřování dokumentu XML, jak je načten do modelu DOM" výše.

## <a name="handling-validation-errors-and-warnings"></a>Zpracování chyb ověřování a upozornění

Při ověřování dat XML načtených v modelu DOM jsou hlášeny chyby ověřování schématu XML. Zobrazí se oznámení o všech chybách ověřování schématu při ověřování dat XML při jejich načítání nebo při ověřování dříve neověřeného dokumentu XML.

Chyby ověřování jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler>. <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> <xref:System.Xml.Schema.ValidationEventHandler> Pokud byla přiřazena instance nebo předána metodě<xref:System.Xml.Schema.XmlSchemaValidationException> třídy, zpracuje chyby ověřování schématu. v opačném případě je vyvolána při ověřování schématu <xref:System.Xml.Schema.ValidationEventHandler> došlo k chybě.

> [!NOTE]
> Data XML jsou načtena do modelu DOM navzdory chybám ověřování schématu, <xref:System.Xml.Schema.ValidationEventHandler> Pokud nevyvolává výjimku k zastavení procesu.
>
> Upozornění ověřování schématu nejsou hlášeny, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> není příznak určen <xref:System.Xml.XmlReaderSettings> pro objekt.

 Příklady ilustrující rozhraní <xref:System.Xml.Schema.ValidationEventHandler>naleznete v části "ověřování dokumentu XML, jak je načten do modelu DOM" a "ověřování dokumentu XML v modelu DOM" výše.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
