---
title: Sestavování schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: c921331b00fe137d4ad52d62951e8c161768dfae
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711139"
---
# <a name="building-xml-schemas"></a>Sestavování schémat XML
Třídy v oboru názvů <xref:System.Xml.Schema?displayProperty=nameWithType> namapují na struktury definované v doporučeních schématu XML konsorcium World Wide Web (W3C) a lze je použít k sestavení schémat XML v paměti.  
  
## <a name="building-an-xml-schema"></a>Sestavení schématu XML  
 V příkladech kódu, které následují, se používá rozhraní API SOM k sestavení schématu XML pro zákazníky v paměti.  
  
### <a name="creating-element-and-attributes"></a>Vytváření elementů a atributů  
 Příklady kódu sestavují schéma zákazníka z dolní části nahoru, vytváření podřízených prvků, atributů a jejich odpovídajících typů a pak prvků na nejvyšší úrovni.  
  
 V následujícím příkladu kódu `FirstName` a `LastName` prvky a také atribut `CustomerId` schématu zákazníka jsou vytvořeny pomocí <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute> tříd modelu SOM. Kromě <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> vlastností tříd <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute>, které odpovídají atributu "Name" `<xs:element />` a `<xs:attribute />` prvků ve schématu XML, všechny ostatní atributy povolené schématem (`defaultValue`, `fixedValue`, `form`atd.) mají odpovídající vlastnosti v <xref:System.Xml.Schema.XmlSchemaElement> a <xref:System.Xml.Schema.XmlSchemaAttribute>ch třídách.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Vytváření typů schémat  
 Obsah elementů a atributů je definován jejich typy. Chcete-li vytvořit prvky a atributy, jejichž typy jsou jedním z vestavěných typů schémat, vlastnost <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> třídy <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> jsou nastaveny s odpovídajícím kvalifikovaným názvem předdefinovaného typu pomocí třídy <xref:System.Xml.XmlQualifiedName>. Chcete-li vytvořit uživatelsky definovaný typ pro prvky a atributy, je vytvořen nový jednoduchý nebo komplexní typ pomocí třídy <xref:System.Xml.Schema.XmlSchemaSimpleType> nebo <xref:System.Xml.Schema.XmlSchemaComplexType>.  
  
> [!NOTE]
> Chcete-li vytvořit nepojmenované jednoduché nebo komplexní typy, které jsou anonymními podřízenými prvky elementu nebo atributu (pro atributy platí pouze jednoduché typy), nastavte vlastnost <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute> třídy na nepojmenované jednoduché nebo komplexní typ místo vlastnosti <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> třídy <xref:System.Xml.Schema.XmlSchemaElement> nebo <xref:System.Xml.Schema.XmlSchemaAttribute>.  
  
 Schémata XML umožňují odvození anonymních i pojmenovaných jednoduchých typů omezením z jiných jednoduchých typů (předdefinované nebo definované uživatelem) nebo konstruované jako seznam nebo sjednocení jiných jednoduchých typů. Třída <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> slouží k vytvoření jednoduchého typu omezením vestavěné `xs:string` typu. Můžete také použít třídy <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> nebo <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> k vytvoření typu seznamu nebo sjednocení. Vlastnost <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> označuje, zda se jedná o jednoduché omezení typu, seznam nebo sjednocení.  
  
 V následujícím příkladu kódu je typ prvku `FirstName` předdefinovaný typ `xs:string`, typ `LastName` elementu je pojmenovaný jednoduchý typ, který je omezením předdefinovaného `xs:string`typu s hodnotou `MaxLength` omezující vlastnost 20 a typem atributu `CustomerId` je vestavěný typ `xs:positiveInteger`. Element `Customer` je anonymní složitý typ, jehož částice je sekvence `FirstName` a `LastName` prvků a jejichž atributy obsahují atribut `CustomerId`.  
  
> [!NOTE]
> Můžete také použít <xref:System.Xml.Schema.XmlSchemaChoice> nebo <xref:System.Xml.Schema.XmlSchemaAll> třídy jako části složeného typu pro replikaci `<xs:choice />` nebo `<xs:all />` sémantiky.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Vytváření a kompilování schémat  
 V tomto okamžiku byly podřízené prvky a atributy, jejich odpovídající typy a `Customer` element nejvyšší úrovně vytvořeny v paměti pomocí rozhraní API modelu SOM. V následujícím příkladu kódu je prvek schématu vytvořen pomocí třídy <xref:System.Xml.Schema.XmlSchema>, prvky nejvyšší úrovně a typy jsou do něj přidány pomocí vlastnosti <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> a kompletní schéma je zkompilováno pomocí třídy <xref:System.Xml.Schema.XmlSchemaSet> a zapsána do konzoly.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> ověřuje schéma zákazníka proti pravidlům schématu XML a zpřístupňuje vlastnosti kompilace po schématu.  
  
> [!NOTE]
> Všechny vlastnosti kompilace post-Schema-compilation v rozhraní API SOM se liší od post-Schema-Validation-informační sady.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> přidaný do <xref:System.Xml.Schema.XmlSchemaSet> je delegát, který volá metodu zpětného volání `ValidationCallback` pro zpracování upozornění a chyb ověřování schématu.  
  
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
