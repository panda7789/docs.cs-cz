---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: adc1a10bb9acb14ee88589c13e28c49773e42100
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291588"
---
# <a name="building-xml-schemas"></a>Sestavování schémat XML
Třídy v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů se mapují na struktury definované v doporučení schématu xml konsorcium World Wide Web (W3C) a lze je použít k sestavení schémat XML v paměti.  
  
## <a name="building-an-xml-schema"></a>Sestavení schématu XML  
 V příkladech kódu, které následují, se používá rozhraní API SOM k sestavení schématu XML pro zákazníky v paměti.  
  
### <a name="creating-element-and-attributes"></a>Vytváření elementů a atributů  
 Příklady kódu sestavují schéma zákazníka z dolní části nahoru, vytváření podřízených prvků, atributů a jejich odpovídajících typů a pak prvků na nejvyšší úrovni.  
  
 V následujícím příkladu kódu `FirstName` jsou prvky a a `LastName` také `CustomerId` atribut schématu zákazníka vytvořeny pomocí <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> tříd a třídy SOM. Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastností <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> tříd a, které odpovídají atributu "Name" `<xs:element />` `<xs:attribute />` elementů a ve schématu XML, všechny ostatní atributy povolené schématem (,, atd `defaultValue` `fixedValue` `form` .) mají odpovídající vlastnosti v <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídách a.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Vytváření typů schémat  
 Obsah elementů a atributů je definován jejich typy. Chcete-li vytvořit prvky a atributy, jejichž typy jsou jedním z vestavěných typů schémat, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy jsou nastaveny s odpovídajícím kvalifikovaným názvem předdefinovaného typu pomocí <xref:System.Xml.XmlQualifiedName> třídy. Chcete-li vytvořit uživatelsky definovaný typ pro prvky a atributy, je vytvořen nový jednoduchý nebo komplexní typ pomocí <xref:System.Xml.Schema.XmlSchemaSimpleType> třídy or <xref:System.Xml.Schema.XmlSchemaComplexType> .  
  
> [!NOTE]
> Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymními podřízenými prvky elementu nebo atributu (pro atributy platí pouze jednoduché typy), nastavte <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nebo na nepojmenované jednoduché nebo komplexní typ namísto <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> třídy nebo.  
  
 Schémata XML umožňují odvození anonymních i pojmenovaných jednoduchých typů omezením z jiných jednoduchých typů (předdefinované nebo definované uživatelem) nebo konstruované jako seznam nebo sjednocení jiných jednoduchých typů. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>Třída se používá k vytvoření jednoduchého typu omezením vestavěného `xs:string` typu. Můžete také použít <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> třídy nebo k vytvoření typu seznamu nebo sjednocení. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType>Vlastnost označuje, zda se jedná o jednoduché omezení typu, seznam nebo sjednocení.  
  
 V následujícím příkladu kódu `FirstName` je typ prvku vestavěný typ `xs:string` , `LastName` typ prvku je pojmenovaný jednoduchý typ, který je omezením vestavěného typu `xs:string` s `MaxLength` hodnotou omezující vlastnosti 20 a `CustomerId` typem atributu je předdefinovaný typ typu `xs:positiveInteger` . `Customer`Element je anonymní komplexní typ, jehož částice je sekvence `FirstName` `LastName` prvků a a jejichž atributy obsahují `CustomerId` atribut.  
  
> [!NOTE]
> Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> <xref:System.Xml.Schema.XmlSchemaAll> třídy nebo jako části složeného typu pro replikaci `<xs:choice />` nebo `<xs:all />` sémantiku.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Vytváření a kompilování schémat  
 V tomto okamžiku se podřízené prvky a atributy, jejich odpovídající typy a element nejvyšší úrovně `Customer` vytvořily v paměti pomocí rozhraní API modelu SOM. V následujícím příkladu kódu je prvek schématu vytvořen pomocí <xref:System.Xml.Schema.XmlSchema> třídy, prvky nejvyšší úrovně a typy jsou do něj přidány pomocí <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> vlastnosti a kompletní schéma je kompilováno pomocí <xref:System.Xml.Schema.XmlSchemaSet> třídy a zapsána do konzoly.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType>Metoda ověřuje schéma zákazníka proti pravidlům pro schéma XML a zpřístupňuje vlastnosti kompilace po schématu.  
  
> [!NOTE]
> Všechny vlastnosti kompilace post-Schema-compilation v rozhraní API SOM se liší od post-Schema-Validation-informační sady.  
  
 <xref:System.Xml.Schema.ValidationEventHandler>Přidaný do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` pro zpracování upozornění a chyb ověřování schématu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled Modelu objektu schématu XML](xml-schema-object-model-overview.md)
- [Čtení ze schémat XML a zápis do nich](reading-and-writing-xml-schemas.md)
- [Procházení schémat XML](traversing-xml-schemas.md)
- [Úpravy schémat XML](editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](post-schema-compilation-infoset.md)
