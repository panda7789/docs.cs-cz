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
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511458"
---
# <a name="building-xml-schemas"></a>Sestavování schémat XML
Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů mapovat na struktury definované v doporučení schématu XML World Wide Web Consortium (W3C) a slouží k sestavení XML schémata v paměti.  
  
## <a name="building-an-xml-schema"></a>Vytváření schématu XML  
 V příkladech kódu, které následují rozhraní API SOM slouží k vytváření zákazník XML schématu v paměti.  
  
### <a name="creating-element-and-attributes"></a>Vytvoření elementu a atributy  
 Příklady kódu sestavte zákazník schématu zdola nahoru, podřízené prvky, atributy a jejich odpovídající typy nejprve vytvoříte a potom prvky nejvyšší úrovně.  
  
 V následujícím příkladu kódu `FirstName` a `LastName` prvky, stejně jako `CustomerId` atribut schématu zákazníka se vytvoří s použitím <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy SOM. Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které odpovídají atributu "name" `<xs:element />` a `<xs:attribute />` elementy ve schématu XML, všechny ostatní atributy tímhle schématem povolený (`defaultValue`, `fixedValue`, `form`, a tak dále) odpovídající vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Vytváření typů schématu  
 Typy hodnot je definována obsah elementů a atributů. K vytváření elementů a atributů, jejichž typy jsou jedním z typů předdefinovaných schémat <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy se nastavují s odpovídající kvalifikovaný název předdefinovaný typ použití <xref:System.Xml.XmlQualifiedName> třídy. Vytvoření uživatelem definovaného typu pro elementy a atributy, je vytvořený pomocí nového typu jednoduché nebo složité <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
> [!NOTE]
>  K vytvoření nepojmenované jednoduchých nebo složitých typů, které jsou anonymní podřízené objekty daného elementu nebo atributu (pouze jednoduché typy lze použít pro atributy), nastavte <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které nepojmenované jednoduché nebo komplexní typ, místo <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.  
  
 Schémata XML povolit anonymní a pojmenované jednoduché typy mají být odvozené omezením z jiných jednoduché typy (integrované nebo uživatelem definovaný) nebo vytvořen jako seznam nebo sjednocení jiných typů jednoduché. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Třída se používá k vytvoření jednoduchého typu tak, že omezíte předdefinované `xs:string` typu. Můžete také použít <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> tříd pro vytvoření seznamu nebo sjednocení typů. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Vlastnost označuje, zda je omezení jednoduchých typů, seznamu nebo sjednocení.  
  
 V následujícím příkladu kódu `FirstName` předdefinovaný typ je typ prvku `xs:string`, `LastName` pojmenované jednoduchý typ, který představuje omezení typu předdefinovaný typ je typ prvku `xs:string`, s `MaxLength` hodnota omezující vlastnosti 20, a `CustomerId` typ atributu je předdefinovaný typ `xs:positiveInteger`. `Customer` Element je anonymní komplexní typ, jehož částice je sekvenci z `FirstName` a `LastName` elementy a jejichž atributy obsahuje `CustomerId` atribut.  
  
> [!NOTE]
>  Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako částice složitý typ k replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Vytváření a kompilování schémat  
 Na tento bod, podřízené prvky a atributy, jejich odpovídající typy a na nejvyšší úrovni `Customer` element byly vytvořeny pomocí rozhraní API SOM v paměti. V následujícím příkladu kódu je vytvořený element schématu pomocí <xref:System.Xml.Schema.XmlSchema> třídy, prvky nejvyšší úrovně a typy jsou přidány pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastností a dokončení schématu je zkompilován pomocí <xref:System.Xml.Schema.XmlSchemaSet> třídy a do něj zapisovat konzoly.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda ověří zákazníka schématu s pomocí pravidel pro schématu XML a zpřístupní vlastnosti po schema kompilace.  
  
> [!NOTE]
>  Všechny vlastnosti po schema kompilace v rozhraní API SOM se liší od po-schema-ověření – informační sadu.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Přidán do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` schématu ověření upozornění a chyby.  
  
 Tady je příklad úplného kódu a schéma zákazníka zapsána do konzoly.  
  
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
