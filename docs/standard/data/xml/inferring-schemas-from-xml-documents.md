---
title: Odvození schémat z dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b4727ead8abb9b3618f8b9dda8f7a9eb4b2321f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968139"
---
# <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML
Toto téma popisuje způsob použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodit jazyk (XSD) schématu definice schématu XML ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Procesu odvození schématu  
 <xref:System.Xml.Schema.XmlSchemaInference> Třídu <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů se používá ke generování jednoho nebo více schémat jazyk (XSD) definice schématu XML ze struktury dokumentu XML. Vygenerovaný schémata slouží k ověření původního dokumentu XML.  
  
 Jako XML je zpracován dokumentu <xref:System.Xml.Schema.XmlSchemaInference> třídy, <xref:System.Xml.Schema.XmlSchemaInference> třída provede předpoklady o schéma komponenty, které popisují prvky a atributy v dokumentu XML. <xref:System.Xml.Schema.XmlSchemaInference> Třídy také odvodí schéma komponenty omezeným způsobem podle odvození typu nejvíce omezující pro konkrétní elementu nebo atributu. Jak se shromažďují Další informace o dokumentu XML, tato omezení jsou uvolnit podle odvození typů méně omezující. Je nejméně restriktivní typ, který jde odvodit `xs:string`.  
  
 Vezměme si jako příklad následující část dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 V příkladu výše, kdy `attribute1` zjištěn atribut s hodnotou `6` podle <xref:System.Xml.Schema.XmlSchemaInference> procesu, předpokládá se typ `xs:unsignedByte`. Při druhý `parent` nalezen element podle <xref:System.Xml.Schema.XmlSchemaInference> zpracovat, je tak, že upravíte typ, který chcete uvolnit omezení `xs:string` protože hodnotu `attribute1` je atribut `A`. Podobně `minOccurs` atribut pro všechny `child` odvodit ve schématu elementy jsou uvolnit na `minOccurs="0"` protože druhý nadřazený element neobsahuje žádné podřízené prvky.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML  
 <xref:System.Xml.Schema.XmlSchemaInference> Používá třídy, dvě přetížené <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody pro odvození schématu z dokumentu XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k vytvoření schématu podle dokumentu XML. Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá pro odvození schématu, který popisuje několik dokumentů XML. Například může zadat více dokumentů XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda současně vytvořit schéma, které popisuje celou sadu dokumentů XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda odvodí schéma z dokumentu XML, který je součástí <xref:System.Xml.XmlReader> objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt, který obsahuje odvozené schématu. Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda vyhledává <xref:System.Xml.Schema.XmlSchemaSet> jako dokument XML obsažených v objektu pro schéma s stejný cílový obor názvů <xref:System.Xml.XmlReader> zpřesnění existující schéma objektu a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt, který obsahuje odvozené schéma.  
  
 Změny provedené v kontrast schématu jsou založeny na novou strukturu nalezen v dokumentu XML. Například jako provázán dokument XML, předpoklady probíhají o datových typech, najít a vytvořit schéma na základě těchto domněnek. Pokud ale dat dochází na druhý odvození pass, která se liší od původní předpoklad, schéma je kontrast. Následující příklad znázorňuje proces vylepšení.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 V příkladu používá následující soubor `item1.xml`, jako první vstup.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 V příkladu provede `item2.xml` soubor jako druhý vstup:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Když `productID` v první dokument XML, hodnota je zjištěn atribut `123456789` je považován za `xs:unsignedInt` typu. Ale pokud je druhý dokument XML pro čtení a hodnota `A53-246` nenajde, `xs:unsignedInt` typ může již nebude předpokládat, že. Schéma je kontrast a typ `productID` se změní na `xs:string`. Kromě toho `minOccurs` atribut pro `supplierID` prvek je nastaven na `0`, protože druhý dokument XML neobsahuje žádné `supplierID` elementu.  
  
 Následuje schéma odvodit z první dokument XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Následuje schéma odvodit z první dokument XML, kontrast druhý dokument XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Vložené schémata  
 Pokud jazyk (XSD) schématu definice schématu XML vložené dochází během <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> je vyvolána výjimka. Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schémata, která se nesmí Refined  
 Existují W3C XML schématu, která vytvoří jazyk (XSD) schématu definice schématu XML <xref:System.Xml.Schema.XmlSchemaInference> proces nemůže zpracovat, pokud zadaný typ Upřesnit a způsobí vyvolání výjimky. Například komplexní typ, jehož složku nejvyšší úrovně je nic jiného než sekvenci. V schématu objektu modelu (SOM), to odpovídá <xref:System.Xml.Schema.XmlSchemaComplexType> jehož <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> vlastnost není instance <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Pravidla pro odvození typů a struktury uzlů schémat](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Pravidla pro odvození jednoduchých typů](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
