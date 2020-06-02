---
title: Odvození schémat z dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5b0f9bea33346083ce0015fbf3cdfeb0e0ea1181
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287659"
---
# <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML
Toto téma popisuje, jak pomocí <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodit schéma XML schématu definice jazyka (XSD) ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Proces odvození schématu  
 <xref:System.Xml.Schema.XmlSchemaInference>Třída <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů se používá ke generování jednoho nebo více schémat XML Schema Definition Language (XSD) ze struktury dokumentu XML. Vygenerovaná schémata lze použít k ověření původního dokumentu XML.  
  
 V případě, že je dokument XML zpracován <xref:System.Xml.Schema.XmlSchemaInference> třídou, <xref:System.Xml.Schema.XmlSchemaInference> vytvoří třída předpoklady o komponentách schématu, které popisují prvky a atributy v dokumentu XML. <xref:System.Xml.Schema.XmlSchemaInference>Třída také odvodí komponenty schématu omezeného způsobu tím, že odvozuje nejvíc omezující typ pro určitý element nebo atribut. Jak je shromažďováno více informací o dokumentu XML, tato omezení jsou vyzpůsobena odvozením méně omezujících typů. Nejméně omezující typ, který lze odvodit, je `xs:string` .  
  
 Vezměte například následující část dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 V předchozím příkladu, pokud `attribute1` je zjištěn atribut s hodnotou `6` <xref:System.Xml.Schema.XmlSchemaInference> procesu, předpokládá se, že je typu `xs:unsignedByte` . Při zjištění druhého `parent` elementu v <xref:System.Xml.Schema.XmlSchemaInference> procesu je omezení odpojeno změnou typu na, `xs:string` protože hodnota `attribute1` atributu je nyní `A` . Podobně `minOccurs` atribut pro všechny `child` elementy odvozené ve schématu jsou rozvoditelné na, `minOccurs="0"` protože druhý nadřazený prvek nemá žádné podřízené prvky.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML  
 <xref:System.Xml.Schema.XmlSchemaInference>Třída používá dvě přetížené <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody pro odvození schématu z dokumentu XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k vytvoření schématu založeného na dokumentu XML. Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda slouží k odvození schématu, které popisuje více dokumentů XML. Můžete například zakládat více dokumentů XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metody v jednom okamžiku pro vytvoření schématu, které popisuje celou sadu dokumentů XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda odvodí schéma z dokumentu XML obsaženého v <xref:System.Xml.XmlReader> objektu a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schéma. Druhá <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Metoda prohledá <xref:System.Xml.Schema.XmlSchemaSet> objekt pro schéma se stejným cílovým oborem názvů jako dokument XML obsažený v <xref:System.Xml.XmlReader> objektu, obnoví existující schéma a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schéma.  
  
 Změny schématu pro upřesnění jsou založeny na nové struktuře nalezené v dokumentu XML. Například při procházení dokumentu XML, jsou vytvořeny předpoklady týkající se nalezených datových typů a schéma je vytvořeno na základě těchto předpokladů. Nicméně pokud jsou data zjištěna v druhém odvození předání, které se liší od původního předpokladu, schéma je upřesněno. Následující příklad znázorňuje proces upřesnění.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 V příkladu se `item1.xml` jako první vstup použije následující soubor.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Příklad pak převezme `item2.xml` soubor jako druhý vstup:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Při `productID` zjištění atributu v prvním dokumentu XML `123456789` je hodnota typu považována za `xs:unsignedInt` typ. Pokud je však druhý dokument XML čten a hodnota `A53-246` je nalezena, `xs:unsignedInt` typ již nelze předpokládat. Schéma je upřesněno a typ `productID` je změněn na `xs:string` . Kromě toho `minOccurs` atribut pro `supplierID` element je nastaven na `0` , protože druhý dokument XML neobsahuje žádný `supplierID` element.  
  
 Následuje schéma odvoditelné z prvního dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Následuje schéma odvoditelné z prvního dokumentu XML, který je rafinovaný druhým dokumentem XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Vložená schémata  
 Pokud je během procesu zjištěno vložené schéma XML Schema Definition Language (XSD) <xref:System.Xml.Schema.XmlSchemaInference> , <xref:System.Xml.Schema.XmlSchemaInferenceException> je vyvolána výjimka. Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException> .  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schémata, která nelze zdokonalit  
 Existují konstrukce schématu W3C XML, které proces schématu XML pro definici schématu (XSD) <xref:System.Xml.Schema.XmlSchemaInference> nemůže zpracovat, pokud je daný typ upřesněn a způsobí vyvolání výjimky. Například komplexní typ, jehož sestavování nejvyšší úrovně je jakékoli jiné než sekvence. V modelu objektu schématu (SOM) to odpovídá objektu, <xref:System.Xml.Schema.XmlSchemaComplexType> jehož <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> vlastnost není instancí <xref:System.Xml.Schema.XmlSchemaSequence> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model objektu schématu (SOM) XML](xml-schema-object-model-som.md)
- [Odvození schématu XML](inferring-an-xml-schema.md)
- [Pravidla pro odvození typů a struktury uzlů schémat](rules-for-inferring-schema-node-types-and-structure.md)
- [Pravidla pro odvození jednoduchých typů](rules-for-inferring-simple-types.md)
