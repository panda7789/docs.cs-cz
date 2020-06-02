---
title: Informační sada po kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 3bd0c6063fee1fa1a9f046a8be2ebfde07aea9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291510"
---
# <a name="post-schema-compilation-infoset"></a>Informační sada po kompilaci schématu
[Doporučení schématu XML pro konsorcium World Wide Web (W3C)](https://www.w3.org/XML/Schema) se zabývá sadou informací (informační sada), která musí být vystavena pro ověření před schématem a pro kompilaci po sestavení schématu. Model objektu XML schématu (SOM) zobrazuje tuto expozici před a po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> volání metody.  
  
 Informační sada pro ověření před schématem je sestavena během úprav schématu. Informační sada po kompilaci po schématu je generována po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> volání metody, během kompilace schématu a je vystavena jako vlastnosti.  
  
 SOM je objektový model, který představuje ověření předběžného schématu a Infosets kompilace po sestavení. skládá se z tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Všechny vlastnosti čtení a zápisu tříd v <xref:System.Xml.Schema> oboru názvů patří do informační sady předběžného schématu, zatímco všechny vlastnosti třídy v oboru názvů, které jsou jen pro čtení, <xref:System.Xml.Schema> patří do informační sady po kompilaci schématu. Výjimkou z tohoto pravidla jsou následující vlastnosti, které jsou zároveň vlastnostmi sady inverze pro ověřování schématu a vlastností informačního doplňku pro kompilaci po schématu.  
  
|Třída|Vlastnost|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Například <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaComplexType> třídy a mají `BlockResolved` `FinalResolved` vlastnosti a. Tyto vlastnosti jsou použity k uchování hodnot `Block` `Final` vlastností a poté, co bylo schéma kompilováno a ověřeno. `BlockResolved`a `FinalResolved` jsou vlastnosti jen pro čtení, které jsou součástí informační sady po sestavení schématu.  
  
 Následující příklad ukazuje <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> sady třídy po ověření schématu. Před ověřením vlastnost obsahuje `null` odkaz a <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je nastaven na název daného typu. Po ověření se <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> přeloží na platný typ a objekt typu je k dispozici prostřednictvím <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> Vlastnosti.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Model objektu schématu (SOM) XML](xml-schema-object-model-som.md)
