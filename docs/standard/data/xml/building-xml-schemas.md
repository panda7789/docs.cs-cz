---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8c8e1b0d9a79ff22f3194e86cd580f3a7e199b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962031"
---
# <a name="building-xml-schemas"></a>Sestavování schémat XML
Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů se mapují na struktury definované v doporučení schématu XML konsorcium World Wide Web (W3C) a lze je použít k sestavení schémat XML v paměti.  
  
## <a name="building-an-xml-schema"></a>Sestavení schématu XML  
 V příkladech kódu, které následují, se používá rozhraní API SOM k sestavení schématu XML pro zákazníky v paměti.  
  
### <a name="creating-element-and-attributes"></a>Vytváření elementů a atributů  
 Příklady kódu sestavují schéma zákazníka z dolní části nahoru, vytváření podřízených prvků, atributů a jejich odpovídajících typů a pak prvků na nejvyšší úrovni.  
  
 `FirstName` V následujícím příkladu kódu jsou prvky a a `LastName` také `CustomerId` atribut schématu zákazníka vytvořeny pomocí <xref:System.Xml.Schema.XmlSchemaElement> tříd a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy SOM. `<xs:element />` `<xs:attribute />` Kromě vlastností tříd <xref:System.Xml.Schema.XmlSchemaElement> a<xref:System.Xml.Schema.XmlSchemaAttribute> , které odpovídají atributu "Name" elementů a ve schématu XML, všech ostatních atributů povolených schématem ( <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> `defaultValue` ,`fixedValue`, a`form`tak dále )mají<xref:System.Xml.Schema.XmlSchemaAttribute> odpovídající vlastnosti v třídách a.<xref:System.Xml.Schema.XmlSchemaElement>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Vytváření typů schémat  
 Obsah elementů a atributů je definován jejich typy. Chcete-li vytvořit prvky a atributy, jejichž typy jsou jedním z vestavěných typů schémat, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy jsou nastaveny s odpovídajícím kvalifikovaným názvem předdefinovaného typu pomocí <xref:System.Xml.XmlQualifiedName> třídy. Chcete-li vytvořit uživatelsky definovaný typ pro prvky a atributy, je vytvořen nový jednoduchý nebo komplexní typ pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> třídy or. <xref:System.Xml.Schema.XmlSchemaComplexType>  
  
> [!NOTE]
> Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymními podřízenými prvky elementu nebo atributu (pro atributy platí pouze jednoduché typy <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> ), nastavte <xref:System.Xml.Schema.XmlSchemaElement> vlastnost <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nebo na nepojmenované jednoduché nebo komplexní typ, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> místo vlastnosti<xref:System.Xml.Schema.XmlSchemaElement> třídy nebo <xref:System.Xml.Schema.XmlSchemaAttribute> .  
  
 Schémata XML umožňují odvození anonymních i pojmenovaných jednoduchých typů omezením z jiných jednoduchých typů (předdefinované nebo definované uživatelem) nebo konstruované jako seznam nebo sjednocení jiných jednoduchých typů. Třída se používá k vytvoření jednoduchého typu omezením vestavěného `xs:string` typu. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Můžete také použít <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> třídy nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> k vytvoření typu seznamu nebo sjednocení. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Vlastnost označuje, zda se jedná o jednoduché omezení typu, seznam nebo sjednocení.  
  
 `FirstName` V následujícím příkladu kódu je typ prvku vestavěný typ `LastName` `xs:string`, typ prvku je pojmenovaný jednoduchý typ, který je omezením vestavěného typu `xs:string`s `MaxLength` hodnotou omezující vlastnosti 20 a typ atributu je vestavěný typ `xs:positiveInteger`. `CustomerId` Element je anonymní komplexní typ, jehož částice je sekvence `FirstName` prvků a `LastName` a jejichž atributy obsahují `CustomerId` atribut. `Customer`  
  
> [!NOTE]
> Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> třídy nebo <xref:System.Xml.Schema.XmlSchemaAll> jako části složeného typu pro replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Vytváření a kompilování schémat  
 V tomto okamžiku se podřízené prvky a atributy, jejich odpovídající typy a element nejvyšší úrovně `Customer` vytvořily v paměti pomocí rozhraní API modelu SOM. V následujícím příkladu kódu je prvek schématu vytvořen pomocí <xref:System.Xml.Schema.XmlSchema> třídy, prvky nejvyšší úrovně a typy jsou do něj přidány <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> pomocí vlastnosti a kompletní <xref:System.Xml.Schema.XmlSchemaSet> schéma je kompilováno pomocí třídy a zapsána do stromu.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda ověřuje schéma zákazníka proti pravidlům pro schéma XML a zpřístupňuje vlastnosti kompilace po schématu.  
  
> [!NOTE]
> Všechny vlastnosti kompilace post-Schema-compilation v rozhraní API SOM se liší od post-Schema-Validation-informační sady.  
  
 Přidaný do je delegát, který volá metodu `ValidationCallback` zpětného volání pro zpracování upozornění a chyb ověřování schématu. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.ValidationEventHandler>  
  
 Následuje příklad kompletního příkladu kódu a schéma zákazníka zapsané do konzoly.  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
