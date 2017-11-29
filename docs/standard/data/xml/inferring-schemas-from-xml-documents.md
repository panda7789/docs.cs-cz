---
title: "Odvození schémata z dokumentů XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aa4d6d2758392fc48969b08db30b91bdfe0eeaa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-schemas-from-xml-documents"></a>Odvození schémata z dokumentů XML
Toto téma popisuje postup použití <xref:System.Xml.Schema.XmlSchemaInference> třídy pro odvození schématu XML definition language (XSD) schématu ze struktury dokumentu XML.  
  
## <a name="the-schema-inference-process"></a>Proces odvození schématu  
 <xref:System.Xml.Schema.XmlSchemaInference> Třídu <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů se používá ke generování jednoho nebo více schématu XML definition language (XSD) schémat ze struktury dokumentu XML. Vygenerovaný schémata může sloužit k ověření původního dokumentu XML.  
  
 Jako XML dokumentu zpracovává <xref:System.Xml.Schema.XmlSchemaInference> třídy, <xref:System.Xml.Schema.XmlSchemaInference> třída provádí předpoklady o komponenty schématu, které popisují elementů a atributů v dokumentu XML. <xref:System.Xml.Schema.XmlSchemaInference> Třída také odvodí komponenty schématu omezené způsobem podle odvození nejvíc omezující typ pro konkrétní elementu nebo atributu. Jako další informace o dokumentu XML jsou shromažďovány, jsou tyto omezení snížit podle odvození méně omezující typy. Je nejméně omezující typ, který lze odvodit `xs:string`.  
  
 Využít, například následující část dokumentu XML.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 V příkladu výše, kdy `attribute1` zjistil se atributu s hodnotou `6` podle <xref:System.Xml.Schema.XmlSchemaInference> procesu, se předpokládá, bude typu `xs:unsignedByte`. Při druhý `parent` je element kterými <xref:System.Xml.Schema.XmlSchemaInference> procesů, omezení je snížit změnou typ, který má `xs:string` protože hodnota `attribute1` je atribut `A`. Podobně `minOccurs` atribut pro všechny `child` elementy odvodit ve schématu se snížit na `minOccurs="0"` protože druhý nadřazeného elementu nemá žádné podřízené prvky.  
  
## <a name="inferring-schemas-from-xml-documents"></a>Odvození schémata z dokumentů XML  
 <xref:System.Xml.Schema.XmlSchemaInference> Třída používá dva přetížený <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody pro odvození schématu z dokumentu XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k vytvoření schéma založené na dokument XML. Druhý <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda se používá k odvození schéma, které popisuje více dokumentů XML. Například může zadat více dokumentů XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda, jeden v době vytvoření schéma, které popisuje celou sadu dokumentů XML.  
  
 První <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda odvodí schématu z dokumentu XML, který je součástí <xref:System.Xml.XmlReader> objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schématu. Druhý <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> metoda hledání <xref:System.Xml.Schema.XmlSchemaSet> objekt pro schématu s stejný cílový obor názvů jako dokument XML obsažených v <xref:System.Xml.XmlReader> zpřesnění schéma existující objekt a vrátí <xref:System.Xml.Schema.XmlSchemaSet> objekt obsahující odvozené schéma.  
  
 Změny provedené v přesnějších schématu jsou založené na nové struktura nalezen v dokumentu XML. Například jako dokument XML vyčerpán, předpoklady jsou vytvářeny o datových typech, najít a schéma se vytvoří na základě těchto předpokladů. Schéma je přesnějších však v případě dat při druhý odvození průchodu odlišnou od původního předpokladů. Následující příklad znázorňuje proces vylepšení.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 V příkladu přijímá následující soubor, `item1.xml`, jako první vstup.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 V příkladu pak dojde `item2.xml` souboru jako druhý vstup:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Když `productID` atribut se vyskytuje v první dokument XML, hodnota `123456789` předpokládá se, že `xs:unsignedInt` typu. Ale pokud je druhého dokumentu XML pro čtení a hodnota `A53-246` nenajde, `xs:unsignedInt` už předpokládá typ. Schéma je přesnějších a typ `productID` se změní na `xs:string`. Kromě toho `minOccurs` atribut pro `supplierID` element je nastaven na hodnotu `0`, protože druhého dokumentu XML obsahuje Ne `supplierID` elementu.  
  
 Toto je schéma odvodit z první dokument XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Toto je schéma odvodit z první dokument XML, vylepšení podle druhého dokumentu XML.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Vložené schémata  
 Pokud je vložené schéma schématu XML definition language (XSD) došlo během <xref:System.Xml.Schema.XmlSchemaInference> procesu <xref:System.Xml.Schema.XmlSchemaInferenceException> je vyvolána výjimka. Například následující vložené schéma vyvolá <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Schémata, které nelze Refined  
 Koncepty schémat XML W3C, která jsou schéma schématu XML definition language (XSD) <xref:System.Xml.Schema.XmlSchemaInference> proces nemůže zpracovat, pokud daný typ Upřesnit a způsobit, že vyvolání výjimky. Například pro komplexní typ jejichž složku nejvyšší úrovně je jakoukoli jinou hodnotu než sekvenci. Ve schématu objektu modelu (model SOM), odpovídá <xref:System.Xml.Schema.XmlSchemaComplexType> jejichž <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> vlastnost není instance <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [Objektový Model schématu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [Pravidla pro odvození typů uzlů schéma a struktura](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [Pravidla pro jednoduché typy odvození](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
