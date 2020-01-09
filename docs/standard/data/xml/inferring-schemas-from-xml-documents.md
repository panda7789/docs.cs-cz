---
title: Odvození schémat z dokumentů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5c2d997d9006a3f1eb971eac20982b9dd5677ebf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710749"
---
# <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML
Toto téma popisuje, jak použít třídu <xref:System.Xml.Schema.XmlSchemaInference> k odvození schématu XML Schema Definition Language (XSD) ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Proces odvození schématu  
 Třída <xref:System.Xml.Schema.XmlSchemaInference> <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů se používá ke generování jednoho nebo více schémat XML Schema Definition Language (XSD) ze struktury dokumentu XML. Vygenerovaná schémata lze použít k ověření původního dokumentu XML.  
  
 V případě, že je dokument XML zpracován třídou <xref:System.Xml.Schema.XmlSchemaInference>, třída <xref:System.Xml.Schema.XmlSchemaInference> vytvoří předpoklady o komponentách schématu, které popisují prvky a atributy v dokumentu XML. Třída <xref:System.Xml.Schema.XmlSchemaInference> také odvodí komponenty schématu omezenému způsobu tím, že odvozuje nejvíc omezující typ pro určitý element nebo atribut. Jak je shromažďováno více informací o dokumentu XML, tato omezení jsou vyzpůsobena odvozením méně omezujících typů. Nejméně omezující typ, který lze odvodit, je `xs:string`.  
  
 Vezměte například následující část dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 Pokud je v předchozím příkladu při výskytu atributu `attribute1` s hodnotou `6` v procesu <xref:System.Xml.Schema.XmlSchemaInference>, předpokládá se, že je typu `xs:unsignedByte`. Když je v procesu <xref:System.Xml.Schema.XmlSchemaInference> nalezen druhý `parent` element, omezení je odpojeno změnou typu na `xs:string`, protože hodnota atributu `attribute1` je nyní `A`. Podobně atribut `minOccurs` pro všechny `child` prvky odvoditelné ve schématu jsou rozvoditelné na `minOccurs="0"`, protože druhý nadřazený prvek nemá žádné podřízené prvky.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Odvození schémat z dokumentů XML  
 Třída <xref:System.Xml.Schema.XmlSchemaInference> používá dvě přetížené metody <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> k odvození schématu z dokumentu XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda slouží k vytvoření schématu založeného na dokumentu XML. Druhá metoda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> slouží k odvození schématu, které popisuje více dokumentů XML. Můžete například zakládat více dokumentů XML do metody <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> jednou v čase pro vytvoření schématu, které popisuje celou sadu dokumentů XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda odvodí schéma z dokumentu XML obsaženého v objektu <xref:System.Xml.XmlReader> a vrátí objekt <xref:System.Xml.Schema.XmlSchemaSet> obsahující odvozené schéma. Druhá metoda <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> prohledá objekt <xref:System.Xml.Schema.XmlSchemaSet> pro schéma se stejným cílovým oborem názvů jako dokument XML obsažený v objektu <xref:System.Xml.XmlReader>, obnoví stávající schéma a vrátí objekt <xref:System.Xml.Schema.XmlSchemaSet> obsahující odvozené schéma.  
  
 Změny schématu pro upřesnění jsou založeny na nové struktuře nalezené v dokumentu XML. Například při procházení dokumentu XML, jsou vytvořeny předpoklady týkající se nalezených datových typů a schéma je vytvořeno na základě těchto předpokladů. Nicméně pokud jsou data zjištěna v druhém odvození předání, které se liší od původního předpokladu, schéma je upřesněno. Následující příklad znázorňuje proces upřesnění.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 V příkladu se jako první vstup použije následující soubor `item1.xml`.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Příklad poté převezme soubor `item2.xml` jako jeho druhý vstup:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Při zjištění atributu `productID` v prvním dokumentu XML je hodnota `123456789` považována za typ `xs:unsignedInt`. Pokud je však druhý dokument XML čten a je nalezena hodnota `A53-246`, typ `xs:unsignedInt` již nelze předpokládat. Schéma je rafinované a typ `productID` je změněn na `xs:string`. Kromě toho atribut `minOccurs` elementu `supplierID` je nastaven na `0`, protože druhý dokument XML neobsahuje žádný `supplierID` element.  
  
 Následuje schéma odvoditelné z prvního dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Následuje schéma odvoditelné z prvního dokumentu XML, který je rafinovaný druhým dokumentem XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Vložená schémata  
 Pokud se během procesu <xref:System.Xml.Schema.XmlSchemaInference> vyskytne vložené schéma XML Schema Definition Language (XSD), je vyvolána <xref:System.Xml.Schema.XmlSchemaInferenceException>. Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schémata, která nelze zdokonalit  
 Existují konstrukce schématu W3C XML, které se schématem <xref:System.Xml.Schema.XmlSchemaInference> schématu XML (XSD) schématu, pokud je daný typ upřesněn a způsobuje vyvolání výjimky. Například komplexní typ, jehož sestavování nejvyšší úrovně je jakékoli jiné než sekvence. V modelu objektu schématu (SOM) odpovídá <xref:System.Xml.Schema.XmlSchemaComplexType>, jehož vlastnost <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> není instancí <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Pravidla pro odvození typů a struktury uzlů schémat](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Pravidla pro odvození jednoduchých typů](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
