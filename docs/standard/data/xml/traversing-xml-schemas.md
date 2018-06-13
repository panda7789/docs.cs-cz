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
ms.openlocfilehash: b02fd72c705d264394b83b89fc7ec802be7e502a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575359"
---
# <a name="traversing-xml-schemas"></a>Procházení schémat XML
Procházení schématu XML pomocí schématu objektu modelu (SOM) rozhraní API poskytuje přístup k prvky, atributy a typy, které jsou uložené v SOM. Procházení XML schéma načtena do rozsahu SOM je také prvním krokem při úpravě schématu XML pomocí rozhraní API SOM.  
  
## <a name="traversing-an-xml-schema"></a>Procházení schématu XML  
 Následující vlastnosti <xref:System.Xml.Schema.XmlSchema> třída poskytovat přístup ke kolekci všechny globální položky, které jsou přidány do schématu XML.  
  
|Vlastnost|Typ objektu, které jsou uložené v kolekci nebo pole|  
|--------------|---------------------------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, nebo <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> (poskytuje přístup ke všem globální úrovni prvky, atributy a typy).|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> (poskytuje přístup k atributy, které nepatří do oboru názvů schématu)|  
  
> [!NOTE]
>  Všechny vlastnosti uvedené v tabulce výše, s výjimkou <xref:System.Xml.Schema.XmlSchema.Items%2A> vlastnost, jsou vlastnosti po-Schema-kompilace-informační sadu (PSCI), které nejsou k dispozici, dokud nebude schéma sestaven. <xref:System.Xml.Schema.XmlSchema.Items%2A> Je vlastnost vedlejší schema kompilace, které je možné před schématu je kompilovaná upravovat všechny globální úrovni prvky, atributy a typy.  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> Vlastnost poskytuje přístup k všechny atributy, které nepatří do oboru názvů schématu. Tyto atributy nejsou zpracovaných procesorem schématu.  
  
 Následující příklad kódu ukazuje, procházení schéma zákazníka vytvořené v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu. Příklad kódu ukazuje procházení schématu pomocí kolekcí popsané výše a zapíše všechny elementy a atributy ve schématu do konzoly.  
  
 Ukázka prochází schéma zákazníka v následujících krocích.  
  
1.  Přidá do nového schématu zákazníka <xref:System.Xml.Schema.XmlSchemaSet> objektu a pak zkompiluje ho. Žádné schéma ověřování upozornění a chyb zjištěných čtení nebo kompilace schématu jsou zpracovávány <xref:System.Xml.Schema.ValidationEventHandler> delegovat.  
  
2.  Načte zkompilovaný <xref:System.Xml.Schema.XmlSchema> objektu z <xref:System.Xml.Schema.XmlSchemaSet> podle iterování přes <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost. Protože je zadané schéma zkompilovat, jsou přístupné po-Schema-kompilace-informační sadu vlastností (PSCI).  
  
3.  Opakována na každé <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekci po-schema-kompilace <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekce zápis název jednotlivých prvků do konzoly.  
  
4.  Získá komplexní typ `Customer` element pomocí <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
5.  Pokud má komplexní typ všechny atributy, získá <xref:System.Collections.IDictionaryEnumerator> výčet přes každý <xref:System.Xml.Schema.XmlSchemaAttribute> a zapíše její název do konzoly.  
  
6.  Získá pořadí částice komplexní typ použití <xref:System.Xml.Schema.XmlSchemaSequence> třídy.  
  
7.  Opakována na každé <xref:System.Xml.Schema.XmlSchemaElement> v <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekce zápis název jednotlivých podřízených prvků do konzoly.  
  
 Níže je úplný příklad kódu.  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> Lze vlastnost <xref:System.Xml.Schema.XmlSchemaSimpleType>, nebo <xref:System.Xml.Schema.XmlSchemaComplexType> Pokud se jedná o jednoduchý typ definovaný uživatelem nebo komplexního typu. Může být také <xref:System.Xml.Schema.XmlSchemaDatatype> Pokud jeden z předdefinovaných datové typy definované v doporučení W3C schématu XML. Ve schématu zákazníka <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> z `Customer` element je <xref:System.Xml.Schema.XmlSchemaComplexType>a `FirstName` a `LastName` prvky jsou <xref:System.Xml.Schema.XmlSchemaSimpleType>.  
  
 Příklad kódu v [schémat XML vytváření](../../../../docs/standard/data/xml/building-xml-schemas.md) tématu použít <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> kolekce přidat atribut `CustomerId` k `Customer` elementu. Toto je vlastnost vedlejší schema kompilace. Je odpovídající vlastnost po-Schema-kompilace-informační sadu <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> kolekce, která obsahuje všechny atributy komplexního typu, včetně těch, které se dědí prostřednictvím odvození typu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
