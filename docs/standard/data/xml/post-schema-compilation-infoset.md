---
title: Informační sadu po schématu kompilace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db1c952003e73beb756567be74ed4eb72612c989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569626"
---
# <a name="post-schema-compilation-infoset"></a>Informační sadu po schématu kompilace
[Doporučení schématu XML World Wide Web Consortium (W3C)](https://www.w3.org/XML/Schema) popisuje sady informace (informační sadu), musí se zveřejnit pro ověření schématu před a po schématu kompilace. Model objektu schématu XML (SOM) zobrazení tato ohrožení před a po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána.  
  
 Informační sadu ověření před schématu je vytvořené během úprav schématu. Po vygenerování informační sadu kompilace po schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána při kompilaci schématu a je k dispozici jako vlastnosti.  
  
 SOM je model objektu, který představuje ověřování schématu před a po schématu kompilace infosets; skládá se ze třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Všechny číst a Zapisovat vlastnosti třídy v <xref:System.Xml.Schema> obor názvů patří do informační ověření před schématu sadu při všechny jen pro čtení vlastnosti třídy v <xref:System.Xml.Schema> obor názvů patří do informační sadu kompilace po schématu. Výjimkou z tohoto pravidla jsou následující vlastnosti, které jsou informační sadu ověřování schématu před a po schématu kompilace informační sadu vlastností.  
  
|Třída|Vlastnost|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Například <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaComplexType> třídy oba mají `BlockResolved` a `FinalResolved` vlastnosti. Tyto vlastnosti jsou používané pro udržení hodnoty `Block` a `Final` vlastnosti po schématu byl zkompilován a ověřit. `BlockResolved` a `FinalResolved` jsou jen pro čtení vlastnosti, které jsou součástí informační sadu kompilace po schématu.  
  
 Následující příklad ukazuje <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> třídy sady po ověření schématu. Před ověřování, obsahuje vlastnost `null` odkaz a <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je nastavena na název typu nejistá. Po ověření <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je přeložit na platný typ, a objekt typu je k dispozici prostřednictvím <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
