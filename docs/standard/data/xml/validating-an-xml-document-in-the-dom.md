---
title: Ověřování dokumentu XML v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 949dc52c332b17784b0e1851d178465fe4881b6f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287633"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

<xref:System.Xml.XmlDocument>Třída neověřuje XML v model DOM (Document Object Model) (DOM) proti schématu XSD (XML Schema Definition Language) nebo definici typu dokumentu (DTD) ve výchozím nastavení. XML je ověřeno pouze ve správném formátu.

Chcete-li ověřit XML v modelu DOM, můžete ověřit XML, jak je načten do modelu DOM předáním schématu – ověření <xref:System.Xml.XmlReader> do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument> třídy, nebo ověření dříve neověřeného dokumentu XML v modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Ověření dokumentu XML, jak je načteno do modelu DOM

<xref:System.Xml.XmlDocument>Třída ověřuje data XML, když jsou načtena do modelu DOM při ověřování <xref:System.Xml.XmlReader> je předán <xref:System.Xml.XmlDocument.Load%2A> metodě <xref:System.Xml.XmlDocument> třídy.

Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Vytvoření schématu XML – ověření objektu XmlReader

Chcete-li vytvořit schéma XML – ověřování <xref:System.Xml.XmlReader> , postupujte podle těchto kroků.

1. Vytvořte novou <xref:System.Xml.XmlReaderSettings> instanci.

2. Přidejte schéma XML do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> instance.

3. Zadejte `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A> .

4. Volitelně můžete zadat <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> a a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> zpracovat chyby ověřování schématu a upozornění zjištěná během ověřování.

5. Nakonec předejte <xref:System.Xml.XmlReaderSettings> objekt do <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> třídy spolu s dokumentem XML a vytvořte ověřování schématu <xref:System.Xml.XmlReader> .

### <a name="example"></a>Příklad

V následujícím příkladu kódu ověřování schématu <xref:System.Xml.XmlReader> ověřuje XML data načtená do modelu DOM. V dokumentu XML jsou provedeny neplatné změny a potom se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Příklad přebírá `contosoBooks.xml` soubor jako vstup.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Příklad také přebírá `contosoBooks.xsd` soubor jako vstup.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Při ověřování dat XML při jejich načítání do modelu DOM Vezměte v úvahu následující skutečnosti.

- Ve výše uvedeném příkladu <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> je volána při každém zjištění neplatného typu. Pokud není <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nastavena při ověřování <xref:System.Xml.XmlReader> , <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána výjimka, když <xref:System.Xml.XmlDocument.Load%2A> je volána, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v rámci ověřování schématu.

- Při načtení dokumentu XML do <xref:System.Xml.XmlDocument> objektu s přidruženým schématem, které definuje výchozí hodnoty, <xref:System.Xml.XmlDocument> zpracovává tyto výchozí hodnoty, jako by se zobrazily v dokumentu XML. To znamená, že <xref:System.Xml.XmlReader.IsEmptyElement%2A> vlastnost vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ze schématu. I když v dokumentu XML, byl napsán jako prázdný prvek.

## <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

<xref:System.Xml.XmlDocument.Validate%2A>Metoda <xref:System.Xml.XmlDocument> třídy ověřuje data XML načtená v modelu DOM proti schématům ve <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> vlastnosti objektu. Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

Následující příklad je podobný příkladu v tématu "ověřování dokumentu XML při jeho načtení do modelu DOM" výše. V tomto příkladu není dokument XML ověřen, protože je načten do modelu DOM, ale je ověřen poté, co byl načten do modelu DOM pomocí <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> třídy. <xref:System.Xml.XmlDocument.Validate%2A>Metoda ověří dokument XML proti schématům XML obsaženým ve <xref:System.Xml.XmlDocument.Schemas%2A> vlastnosti <xref:System.Xml.XmlDocument> . V dokumentu XML jsou následně provedeny neplatné změny a pak se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Příklad přijímá jako vstup `contosoBooks.xml` soubory a, `contosoBooks.xsd` na které se říká "ověřování dokumentu XML, jak je načten do modelu DOM" výše.

## <a name="handling-validation-errors-and-warnings"></a>Zpracování chyb ověřování a upozornění

Při ověřování dat XML načtených v modelu DOM jsou hlášeny chyby ověřování schématu XML. Zobrazí se oznámení o všech chybách ověřování schématu při ověřování dat XML při jejich načítání nebo při ověřování dříve neověřeného dokumentu XML.

Chyby ověřování jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> . Pokud <xref:System.Xml.Schema.ValidationEventHandler> byla přiřazena <xref:System.Xml.XmlReaderSettings> instance nebo předána <xref:System.Xml.XmlDocument.Validate%2A> metodě <xref:System.Xml.XmlDocument> třídy, zpracuje <xref:System.Xml.Schema.ValidationEventHandler> chyby ověřování schématu. v opačném případě <xref:System.Xml.Schema.XmlSchemaValidationException> je vyvolána při zjištění chyby ověřování schématu.

> [!NOTE]
> Data XML jsou načtena do modelu DOM navzdory chybám ověřování schématu, pokud <xref:System.Xml.Schema.ValidationEventHandler> nevyvolává výjimku k zastavení procesu.
>
> Upozornění ověřování schématu nejsou hlášeny, pokud <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> není příznak určen pro <xref:System.Xml.XmlReaderSettings> objekt.

 Příklady ilustrující rozhraní naleznete v <xref:System.Xml.Schema.ValidationEventHandler> části "ověřování dokumentu XML, jak je načten do modelu DOM" a "ověřování dokumentu XML v modelu DOM" výše.

## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Zpracování dat XML pomocí modelu DOM](process-xml-data-using-the-dom-model.md)
- [Práce se schématy XML](working-with-xml-schemas.md)
