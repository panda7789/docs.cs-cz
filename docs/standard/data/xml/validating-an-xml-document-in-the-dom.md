---
title: Ověřování dokumentu XML v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 93686ddf1afff76926e77acdbf5aa58e93d6cb77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710034"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

Třída<xref:System.Xml.XmlDocument> neověřuje XML v model DOM (Document Object Model) (DOM) proti schématu XSD (XML Schema Definition Language) nebo definici typu dokumentu (DTD) ve výchozím nastavení. XML je ověřeno pouze jako správně vytvořený.

Chcete-li ověřit XML v modelu DOM, můžete ověřit XML, jak je načteno do modelu DOM předáním schématu <xref:System.Xml.XmlReader> ověřováním do metody <xref:System.Xml.XmlDocument.Load%2A> třídy <xref:System.Xml.XmlDocument>, nebo ověřením dříve neověřeného dokumentu XML v modelu DOM pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Ověření dokumentu XML, jak je načteno do modelu DOM

Třída <xref:System.Xml.XmlDocument> ověřuje data XML, když jsou načtena do modelu DOM, když je ověřování <xref:System.Xml.XmlReader> předáno metodě <xref:System.Xml.XmlDocument.Load%2A> třídy <xref:System.Xml.XmlDocument>.

Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Vytvoření schématu XML – ověření objektu XmlReader

Chcete-li vytvořit schéma XML – ověřování <xref:System.Xml.XmlReader>, postupujte podle těchto kroků.

1. Vytvořte novou instanci <xref:System.Xml.XmlReaderSettings>.

2. Přidejte schéma XML do vlastnosti <xref:System.Xml.XmlReaderSettings.Schemas%2A> instance <xref:System.Xml.XmlReaderSettings>.

3. Jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>zadejte `Schema`.

4. Volitelně můžete zadat <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> pro zpracování chyb ověřování schématu a upozornění zjištěná během ověřování.

5. Nakonec předejte objekt <xref:System.Xml.XmlReaderSettings> do metody <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader> spolu s dokumentem XML a vytvořte <xref:System.Xml.XmlReader>pro ověřování schématu.

### <a name="example"></a>Příklad

V následujícím příkladu kódu je ověřování schématu <xref:System.Xml.XmlReader> ověřuje XML data načtená do modelu DOM. V dokumentu XML jsou provedeny neplatné změny a potom se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

V příkladu se jako vstup používá soubor `contosoBooks.xml`.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Příklad také přebírá soubor `contosoBooks.xsd` jako vstup.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Při ověřování dat XML při jejich načítání do modelu DOM Vezměte v úvahu následující skutečnosti.

- V předchozím příkladu je <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> volána při každém zjištění neplatného typu. Pokud <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> není nastavena při ověřování <xref:System.Xml.XmlReader>, je vyvolána <xref:System.Xml.Schema.XmlSchemaValidationException> při volání <xref:System.Xml.XmlDocument.Load%2A>, pokud jakýkoli typ atributu nebo elementu neodpovídá odpovídajícímu typu zadanému v ověřovacím schématu.

- Při načtení dokumentu XML do objektu <xref:System.Xml.XmlDocument> s přidruženým schématem, které definuje výchozí hodnoty, <xref:System.Xml.XmlDocument> zachází s těmito výchozími hodnotami, jako by se zobrazily v dokumentu XML. To znamená, že vlastnost <xref:System.Xml.XmlReader.IsEmptyElement%2A> vždy vrátí `false` pro prvek, který byl nastaven jako výchozí ze schématu. I když v dokumentu XML, byl napsán jako prázdný prvek.

## <a name="validating-an-xml-document-in-the-dom"></a>Ověřování dokumentu XML v modelu DOM

Metoda <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument> ověřuje data XML načtená v modelu DOM proti schématům ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> objektu <xref:System.Xml.XmlDocument>. Po úspěšném ověření se použije výchozí nastavení schématu, textové hodnoty se v případě potřeby převedou na atomické hodnoty a informace o typu se přidruží k položkám ověřovaných informací. V důsledku toho typované XML data nahradí dříve netypové XML data.

Následující příklad je podobný příkladu v tématu "ověřování dokumentu XML při jeho načtení do modelu DOM" výše. V tomto příkladu není dokument XML ověřen, protože je načten do modelu DOM, ale je ověřen poté, co byl načten do modelu DOM pomocí metody <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>. Metoda <xref:System.Xml.XmlDocument.Validate%2A> ověří dokument XML proti schématům XML obsaženým ve vlastnosti <xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument>. V dokumentu XML jsou následně provedeny neplatné změny a pak se dokument znovu ověří a způsobuje chyby při ověřování schématu. Nakonec se jedna z chyb opravuje a pak je částečně ověřená část dokumentu XML.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Příklad přijímá jako vstup soubory `contosoBooks.xml` a `contosoBooks.xsd`, na které se říká "ověřování dokumentu XML, jak je načten do modelu DOM" výše.

## <a name="handling-validation-errors-and-warnings"></a>Zpracování chyb ověřování a upozornění

Při ověřování dat XML načtených v modelu DOM jsou hlášeny chyby ověřování schématu XML. Zobrazí se oznámení o všech chybách ověřování schématu při ověřování dat XML při jejich načítání nebo při ověřování dříve neověřeného dokumentu XML.

Chyby ověřování jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler>. Pokud byla <xref:System.Xml.Schema.ValidationEventHandler> přiřazena k instanci <xref:System.Xml.XmlReaderSettings> nebo předána metodě <xref:System.Xml.XmlDocument.Validate%2A> třídy <xref:System.Xml.XmlDocument>, <xref:System.Xml.Schema.ValidationEventHandler> bude zpracovávat chyby ověřování schématu; v opačném případě je při zjištění chyby ověřování schématu vyvolána <xref:System.Xml.Schema.XmlSchemaValidationException>.

> [!NOTE]
> Data XML jsou načtena do modelu DOM navzdory chybám ověřování schématu, pokud <xref:System.Xml.Schema.ValidationEventHandler> nevyvolává výjimku k zastavení procesu.
>
> Upozornění ověřování schématu nejsou hlášeny, pokud není pro objekt <xref:System.Xml.XmlReaderSettings> zadán příznak <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings>.

 Příklady ilustrující <xref:System.Xml.Schema.ValidationEventHandler>naleznete v části "ověřování dokumentu XML, jak je načten do modelu DOM" a "ověřování dokumentu XML v modelu DOM" výše.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
