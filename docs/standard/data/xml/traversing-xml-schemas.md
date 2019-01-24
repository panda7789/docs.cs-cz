---
title: Procházení schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c587f4248205251824be851c135d93784e86c2f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646630"
---
# <a name="traversing-xml-schemas"></a>Procházení schémat XML
Procházení schématu XML pomocí schématu objektu modelu (SOM) rozhraní API poskytuje přístup k elementů, atributů a typy, které jsou uložené v SOM. Procházení XML schéma nahrán SOM je také prvním krokem při úpravách schématu XML pomocí rozhraní API SOM.  
  
## <a name="traversing-an-xml-schema"></a>Procházení schématu XML  
 Následující vlastnosti <xref:System.Xml.Schema.XmlSchema> třídy poskytují přístup ke kolekci všechny globální položky přidané do schématu XML.  
  
|Vlastnost|Typ objektu uložených v kolekci nebo pole|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, nebo <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (poskytuje přístup ke všem globální úrovni elementů, atributů a typy).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (poskytuje přístup k atributům, které nepatří do oboru názvů schématu)|  
  
> [!NOTE]
>  Všechny vlastnosti uvedené v tabulce výše, s výjimkou <xref:System.Xml.Schema.XmlSchema.Items%2A> vlastnosti, jsou vlastnosti po-Schema-kompilace – informační sada (PSCI), které nejsou k dispozici, dokud schématu byl zkompilován. <xref:System.Xml.Schema.XmlSchema.Items%2A> Vlastností je vlastnost předprodukční schema kompilace, která lze využít, než byl zkompilován schématu upravovat globální úrovni elementů, atributů a typy.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Vlastnost poskytuje přístup ke všem atributům, které nepatří do oboru názvů schématu. Tyto atributy nejsou zpracovány procesorem schématu.  
  
 Následující příklad kódu ukazuje, procházení zákazníka schéma se vytvořilo v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu. Příklad kódu ukazuje, procházení schématu pomocí kolekce popsané výše a zapisuje všechny elementy a atributy do schématu do konzoly.  
  
 Ukázka prochází schématu zákazníka v následujících krocích.  
  
1.  Přidá schématu zákazníků na novou <xref:System.Xml.Schema.XmlSchemaSet> objekt a potom jej zkompiluje. Žádné schéma ověření upozornění a chyb zjištěných čtení nebo kompilaci schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> pomocí provádí iterace <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože kompilaci schématu, po-Schema-kompilace – informační sadu vlastností (PSCI) jsou přístupné.  
  
3.  Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekce po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> výpis do konzoly název každého prvku kolekce.  
  
4.  Získá komplexní typ `Customer` pomocí elementu <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
5.  Pokud komplexní typ obsahuje všechny atributy, získá <xref:System.Collections.IDictionaryEnumerator> jak vytvořit výčet každý <xref:System.Xml.Schema.XmlSchemaAttribute> a svým jménem zapisuje do konzoly.  
  
6.  Získá částice sequence komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.  
  
7.  Iteruje přes každý <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce zápisu názvu jednotlivých podřízených prvků do konzoly.  
  
 Tady je příklad úplného kódu.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Vlastnost může být <xref:System.Xml.Schema.XmlSchemaSimpleType>, nebo <xref:System.Xml.Schema.XmlSchemaComplexType> Pokud je uživatelský jednoduchý typ. nebo komplexního typu. Může být <xref:System.Xml.Schema.XmlSchemaDatatype> Pokud jeden z předdefinované datové typy definované v doporučení W3C XML schématu. Ve schématu zákazníků <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> z `Customer` element je <xref:System.Xml.Schema.XmlSchemaComplexType>a `FirstName` a `LastName` prvky jsou <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Příklad kódu v [sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md) téma používá <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekce přidejte atribut `CustomerId` k `Customer` elementu. Toto je vlastnost předprodukční schema kompilace. Je odpovídající vlastnost po-Schema-kompilace – informační sadu <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> kolekce, která obsahuje všechny atributy komplexní typ, včetně těch, které jsou zděděny prostřednictvím odvození typu.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
