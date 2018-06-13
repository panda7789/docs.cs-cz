---
title: Vytváření XML schémata
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ed02680831302880e2bfc02b21ea61303b92a3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576819"
---
# <a name="building-xml-schemas"></a>Vytváření XML schémata
Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů namapovat struktury definované v doporučení schématu XML World Wide Web Consortium (W3C) a slouží k vytvoření XML schémata v paměti.  
  
## <a name="building-an-xml-schema"></a>Vytváření schématu XML  
 Příklady kódu, které následují rozhraní API SOM slouží k vytvoření zákazníka XML schématu v paměti.  
  
### <a name="creating-element-and-attributes"></a>Vytváření elementu a atributy  
 Příklady kódu sestavení zákazník schématu zdola nahoru, vytváření podřízené prvky, atributy a jejich odpovídající typy první a pak nejvyšší úrovně elementy.  
  
 V následujícím příkladu kódu `FirstName` a `LastName` prvky, a taky `CustomerId` atribut zákazníka schématu, které jsou vytvořené pomocí <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy SOM. Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy, které odpovídají podle atributu "name" `<xs:element />` a `<xs:attribute />` elementy ve schématu XML, všechny atributy povolena schématem (`defaultValue`, `fixedValue`, `form`a tak dále) mít odpovídající vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Vytváření typy schémat  
 Obsah elementů a atributů je definována jejich typy. K vytvoření elementů a atributů, jejichž typy jsou jeden z předdefinovaných schémat typů <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy se nastavují s odpovídající úplný název předdefinovaný typ pomocí <xref:System.Xml.XmlQualifiedName> – třída. Vytvoření typu uživatelem definované pro elementy a atributy, je vytvořený nový jednoduché nebo komplexní typ, pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType> třídy.  
  
> [!NOTE]
>  Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymní podřízené položky elementu nebo atributu (pouze jednoduché typy použít pro atributy), nastavit <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nepojmenované jednoduché nebo komplexní typ, místo <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy.  
  
 Schémata XML povolit také oba anonymní a pojmenované jednoduché typy pocházet omezením z dalších jednoduchý typů (předdefinovaných nebo uživatelsky definovaných) nebo sestavený jako seznam nebo sjednocení dalších jednoduchý typů. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Třída se používá k vytvoření jednoduchého typu omezením integrované `xs:string` typu. Můžete také <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> třídy pro vytvoření seznamu nebo sjednocení typů. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Vlastnost označuje, zda se jedná o jednoduchý typ omezení, seznamu nebo union.  
  
 V následujícím příkladu kódu `FirstName` předdefinovaný typ je typ elementu `xs:string`, `LastName` pojmenované jednoduchý typ, který je omezení předdefinovaný typ je typ elementu `xs:string`, s `MaxLength` hodnota omezující vlastnosti 20, a `CustomerId` typ atributu je předdefinovaný typ `xs:positiveInteger`. `Customer` Element je anonymní komplexní typ, jejichž částice je sekvenci z `FirstName` a `LastName` elementy a atributy, jejichž obsahuje `CustomerId` atribut.  
  
> [!NOTE]
>  Můžete také <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako částice komplexního typu k replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Vytváření a kompilování schémat.  
 V tomto bodu, podřízené elementy a atributy, jejich odpovídající typy a nejvyšší úrovně `Customer` element byla vytvořena pomocí rozhraní API SOM v paměti. V následujícím příkladu kódu je vytvořený pomocí elementu schema <xref:System.Xml.Schema.XmlSchema> třídy, nejvyšší úrovně prvky a typy jsou přidány do pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastností a dokončení schématu je kompilovat, pomocí <xref:System.Xml.Schema.XmlSchemaSet> – třída a zapisují do Konzola.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda ověří schéma zákazníka proti pravidla pro schéma XML a zpřístupní po schema kompilace vlastnosti.  
  
> [!NOTE]
>  Všechny vlastnosti po schema kompilace v rozhraní API SOM se liší od po-schema-ověření-informační sadu.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Přidán do <xref:System.Xml.Schema.XmlSchemaSet> je delegáta, který volá metodu zpětného volání `ValidationCallback` pro zpracování chyby a varování ověřování schématu.  
  
 Níže je úplný příklad kódu a schéma zákazníka zapsána do konzoly.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Čtení ze schémat XML a zápis do nich](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
