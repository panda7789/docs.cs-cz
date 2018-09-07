---
title: Informační sada po kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e7892289248c9651b529bcc68d7228b8babb28a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083816"
---
# <a name="post-schema-compilation-infoset"></a>Informační sada po kompilaci schématu
[Doporučení schématu XML World Wide Web Consortium (W3C)](https://www.w3.org/XML/Schema) popisuje informace o sadě (informační sadu), který musí být vystavené pro ověřování schématu před a po kompilaci schématu. Model objektu schématu XML (SOM) zobrazení této vystavení před a po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána.  
  
 Informační sada předběžné schéma ověření je vytvořený při úpravách schématu. Informační sada po kompilaci schématu je generován poté <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána v průběhu kompilace schématu a je přístupný jako vlastnosti.  
  
 Objektový model, který představuje ověřování schématu před a po kompilaci schématu infosets; je SOM skládá se ze tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Všechny číst a Zapisovat vlastnosti třídy v <xref:System.Xml.Schema> obor názvů patřit do informační předběžné schéma ověření sadu při všechny vlastnosti jen pro čtení třídy v <xref:System.Xml.Schema> obor názvů patřit do informační sada po kompilaci schématu. Výjimkou z tohoto pravidla jsou následující vlastnosti, které jsou informační sadu předběžné schéma ověření a vlastnosti informační sada po kompilaci schématu.  
  
|Třída|Vlastnost|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Například <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaComplexType> obsahují `BlockResolved` a `FinalResolved` vlastnosti. Tyto vlastnosti se používají k uložení hodnoty `Block` a `Final` vlastnosti po schématu byl zkompilován a ověřit. `BlockResolved` a `FinalResolved` jsou vlastnosti jen pro čtení, které jsou součástí informační sada po kompilaci schématu.  
  
 Následující příklad ukazuje <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> třídy sady po ověření schématu. Před ověřování, obsahuje vlastnost `null` odkaz a <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je nastavena na název typu nejistá. Po ověření <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> je přeložit na platný typ, typ objektu je k dispozici <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> vlastnost.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
