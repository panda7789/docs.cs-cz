---
title: Schéma kontraktů dat – referenční informace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57ccc812aab5df0a9acd99bdcde327d56e4bad8d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="data-contract-schema-reference"></a>Schéma kontraktů dat – referenční informace
Toto téma popisuje některé z schéma XML (XSD) používané <xref:System.Runtime.Serialization.DataContractSerializer> k popisu common language runtime (CLR) typy pro serializaci XML.  
  
## <a name="datacontractserializer-mappings"></a>Mapování DataContractSerializer  
 `DataContractSerializer` Mapuje typy CLR XSD při exportu metadata z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby pomocí koncový bod metadat nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Také mapuje XSD typy CLR při Svcutil.exe se používá pro přístup k webové služby popis Language (WSDL) nebo XSD dokumentů a generovat kontrakty dat pro služby nebo klientů.  
  
 Pouze instance schématu XML, které v souladu s požadavky uvedené v tomto dokumentu lze mapovat na typy CLR pomocí `DataContractSerializer`.  
  
### <a name="support-levels"></a>Úrovně podpory  
 `DataContractSerializer` Poskytuje následující úrovně podpory pro danou funkci schématu XML:  
  
-   **Podporované**. Je explicitní mapování z této funkce se CLR typy atributů (nebo obě) pomocí `DataContractSerializer`.  
  
-   **Ignorovat**. Tato funkce je povolena v schémata importovat pomocí `DataContractSerializer`, ale nemá žádný vliv na generování kódu.  
  
-   **Je zakázané**. `DataContractSerializer` Nepodporuje import schématu pomocí funkce. Například Svcutil.exe při přístupu k WSDL se schématem, které používá funkci, se vrátí k používání <xref:System.Xml.Serialization.XmlSerializer> místo. Toto je ve výchozím nastavení.  
  
## <a name="general-information"></a>Obecné informace  
  
-   Obor názvů schématu je popsána v [schématu XML](http://go.microsoft.com/fwlink/?LinkId=95475). V tomto dokumentu se používá předpona "xs".  
  
-   Žádné atributy k oboru názvů na schéma se ignorují.  
  
-   Žádné poznámky (s výjimkou těch popsaných v tomto dokumentu) se ignorují.  
  
### <a name="xsschema-attributes"></a>\<xs:Schema >: atributy  
  
|Atribut|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Ignorovat.|  
|`blockDefault`|Ignorovat.|  
|`elementFormDefault`|Musí být kvalifikovaný. Všechny elementy musí být kvalifikovaný pro schématu jsou podporováni `DataContractSerializer`. To můžete udělat buď nastavení xs:schema/@elementFormDefault "kvalifikovaný" nebo nastavením xs:element/@form na "kvalifikovaný" na každý jednotlivý prvek deklarace.|  
|`finalDefault`|Ignorovat.|  
|`Id`|Ignorovat.|  
|`targetNamespace`|Podporované a mapované na obor názvů kontraktu dat. Pokud tento atribut nezadá, použije se prázdný obor názvů. Nemůže být vyhrazený obor názvů http://schemas.microsoft.com/2003/10/Serialization/.|  
|`version`|Ignorovat.|  
  
### <a name="xsschema-contents"></a>\<xs:Schema >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`include`|Podporováno. `DataContractSerializer` podporuje xs: zahrnout a xs:import. Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje při načítání metadat z místního souboru. Seznam souborů schématu musí být předán přes mechanismus out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumenty jsou ignorovány.|  
|`redefine`|Je zakázané. Použití `xs:redefine` je zakázána `DataContractSerializer` z bezpečnostních důvodů: `x:redefine` vyžaduje `schemaLocation` -li být zahájen. V některých případech Svcutil.exe pomocí kontraktu omezuje použití `schemaLocation`.|  
|`import`|Podporováno. `DataContractSerializer` podporuje `xs:include` a `xs:import`. Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje při načítání metadat z místního souboru. Seznam souborů schématu musí být předán přes mechanismus out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumenty jsou ignorovány.|  
|`simpleType`|Podporováno. Najdete v článku `xs:simpleType` oddílu.|  
|`complexType`|Nepodporuje mapuje kontrakty dat. Najdete v článku `xs:complexType` oddílu.|  
|`group`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.|  
|`attributeGroup`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.|  
|`element`|Podporováno. Najdete v části globální Element deklarace (NĚNÁ).|  
|`attribute`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nelze na něj odkazovat z uvnitř `complexType` nebo jiné podporované konstrukce.|  
|`notation`|Ignorovat.|  
  
## <a name="complex-types--xscomplextype"></a>Komplexní typy – \<xs:complexType >  
  
### <a name="general-information"></a>Obecné informace  
 Každý komplexní typ \<xs:complexType > mapuje kontraktu dat.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`abstract`|Musí mít hodnotu false (výchozí).|  
|`block`|Je zakázané.|  
|`final`|Ignorovat.|  
|`id`|Ignorovat.|  
|`mixed`|Musí mít hodnotu false (výchozí).|  
|`name`|Podporované a mapované na název kontraktu dat. Pokud v názvu tečky, je proveden pokus o namapovat typ vnitřní typu. Například komplexní typ s názvem `A.B` mapuje kontraktu dat typ, který je vnitřní druh typu s názvem kontraktu dat. `A`, ale jenom v případě, že tyto údaje smlouvy typu existuje. Více než jedné úrovně vnoření je možné: například `A.B.C` může být vnitřní typ, ale jenom v případě `A` a `A.B` obě neexistuje.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleContent`|Rozšíření jsou zakázané.<br /><br /> Omezení je povoleno pouze ze `anySimpleType`.|  
|`complexContent`|Podporováno. Najdete v části "Dědičnosti".|  
|`group`|Je zakázané.|  
|`all`|Je zakázané.|  
|`choice`|Je zakázané|  
|`sequence`|Nepodporuje mapuje datových členů sady kontraktu dat.|  
|`attribute`|Je zakázané, i v případě použití = "prohibited" (s jedinou výjimkou). Jsou podporovány pouze volitelných atributů z oboru názvů schématu standardní serializace. Budou se nemapují do datových členů v kontrakt dat programovací model. V současné době pouze jeden takový atribut má význam a popsané v části ISerializable. Všechny další se ignorují.|  
|`attributeGroup`|Je zakázané. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] verze v1 `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType`.|  
|`anyAttribute`|Je zakázané.|  
|(prázdný)|Mapuje kontraktu dat bez členů data.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<: Sequence > složitý typ: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`id`|Ignorovat.|  
|`maxOccurs`|Musí být 1 (výchozí).|  
|`minOccurs`|Musí být 1 (výchozí).|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<: Sequence > složitý typ: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`element`|Každá instance se mapuje na člena.|  
|`group`|Je zakázané.|  
|`choice`|Je zakázané.|  
|`sequence`|Je zakázané.|  
|`any`|Je zakázané.|  
|(prázdný)|Mapuje kontraktu dat bez členů data.|  
  
## <a name="elements--xselement"></a>Elementy – \<xs:element >  
  
### <a name="general-information"></a>Obecné informace  
 `<xs:element>` může dojít v následujících kontextech:  
  
-   Může dojít v rámci `<xs:sequence>`, který popisuje členem data kontraktu regulární dat (bez kolekce). V takovém případě `maxOccurs` atributu musí být 1. (Není povolena hodnota 0).  
  
-   Může dojít v rámci `<xs:sequence>`, který popisuje členem data kontraktu dat kolekce. V takovém případě `maxOccurs` atributu musí být větší než 1 nebo "bez vazby".  
  
-   Může dojít v rámci `<xs:schema>` jako globální Element deklarace (NĚNÁ).  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:element > s maxOccurs = 1 v rámci \<: Sequence > (datové členy)  
  
|Atribut|Schéma|  
|---------------|------------|  
|`ref`|Je zakázané.|  
|`name`|Nepodporuje mapuje název člena data.|  
|`type`|Podporované, zadejte mapuje datový člen. Další informace najdete v tématu typ nebo primitivní mapování. Pokud není zadané (a element neobsahuje anonymní typ), `xs:anyType` se předpokládá.|  
|`block`|Ignorovat.|  
|`default`|Je zakázané.|  
|`fixed`|Je zakázané.|  
|`form`|Musí být kvalifikovaný. Tento atribut lze nastavit pomocí `elementFormDefault` na `xs:schema`.|  
|`id`|Ignorovat.|  
|`maxOccurs`|1|  
|`minOccurs`|Se mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost datového členu (`IsRequired` platí v případě `minOccurs` 1).|  
|`nillable`|Mapování typu ovlivňuje. V tématu typ nebo primitivní mapování.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:element > s maxOccurs > 1 v rámci \<: Sequence > (kolekce)  
  
-   Se mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
-   V kolekci typů je povolen pouze jeden xs:element v rámci: Sequence.  
  
 Kolekce může být z následujících typů:  
  
-   Regulární kolekce (například polí).  
  
-   Kolekce slovníku (mapování jednu hodnotu na jiný; například <xref:System.Collections.Hashtable>).  
  
-   Jediným rozdílem mezi slovník a pole typu dvojice klíč/hodnota je v generované programovací model. Není schématu poznámky mechanismus, který slouží k označení, že je daný typ kolekce slovníku.  
  
 Pravidla pro `ref`, `block`, `default`, `fixed`, `form`, a `id` atributy jsou stejné jako pro případ jiné kolekce. Ostatní atributy patří v následující tabulce.  
  
|Atribut|Schéma|  
|---------------|------------|  
|`name`|Podporovaná, je přiřazen <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost `CollectionDataContractAttribute` atribut.|  
|`type`|Nepodporuje mapuje na typ uložené v kolekci.|  
|`maxOccurs`|Větší než 1 nebo "bez vazby". Schéma řadiče domény by měli používat "bez vazby".|  
|`minOccurs`|Ignorovat.|  
|`nillable`|Mapování typu ovlivňuje. Tento atribut je ignorován pro kolekce slovníku.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:element > v rámci \<xs:schema > globální deklarace Element  
  
-   Globální Element deklarace (NĚNÁ), má se stejným názvem a oboru názvů jako typu ve schématu, nebo anonymní typ uvnitř sebe, který definuje říká, že je možné přidružit s typem.  
  
-   Export schématu: přidružené GEDs jsou generovány pro každý typ generovaného, jednoduché a komplexní.  
  
-   Deserializace/serializace: přidružené GEDs jsou použity jako kořenové elementy pro typ.  
  
-   Import schématu: přidružené GEDs není vyžadován a jsou ignorovány, pokud se podle následujících pravidel (Pokud se definování typů).  
  
|Atribut|Schéma|  
|---------------|------------|  
|`abstract`|Musí mít hodnotu false pro přidružené GEDs.|  
|`block`|Je zakázané v přidružené GEDs.|  
|`default`|Je zakázané v přidružené GEDs.|  
|`final`|Musí mít hodnotu false pro přidružené GEDs.|  
|`fixed`|Je zakázané v přidružené GEDs.|  
|`id`|Ignorovat.|  
|`name`|Podporováno. Viz definice přidružené GEDs.|  
|`nillable`|Musí být pro přidružené GEDs na hodnotu true.|  
|`substitutionGroup`|Je zakázané v přidružené GEDs.|  
|`type`|Podporované a musí odpovídat typ přidružené přidružené GEDs (pokud element obsahuje anonymní typ).|  
  
### <a name="xselement-contents"></a>\<xs:element >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Ignorovat.|  
|`key`|Ignorovat.|  
|`keyref`|Ignorovat.|  
|(prázdný)|Podporováno.|  
  
 \* Při použití `simpleType` a `complexType,` mapování pro anonymní typy je stejné jako anonymní typy, s tím rozdílem, že neexistuje žádná kontrakty anonymní dat, a tudíž vytvoření kontraktu dat s názvem s názvem odvozené od názvu elementu. Pravidla pro anonymní typy jsou v následujícím seznamu:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Podrobnosti implementace: Pokud `xs:element` název neobsahuje období, anonymního typu se mapuje na typ vnitřní, vnější datového typu kontraktu. Pokud název obsahuje tečky, výsledný typ kontraktu dat je nezávislá (není vnitřní typ).  
  
-   Název kontraktu generované datové vnitřní typu je název kontraktu dat vnější typu, za nímž následuje období, název elementu a řetězce "Typ".  
  
-   Pokud data smluvním vztahu se tento název již existuje, název je jedinečný připojením "1", "2", "3", a tak dále, dokud nebude vytvořen jedinečný název.  
  
## <a name="simple-types---xssimpletype"></a>Jednoduché typy - \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`final`|Ignorovat.|  
|`id`|Ignorovat.|  
|`name`|Podporované, mapuje data název kontraktu.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`restriction`|Podporováno. Kontrakty se mapuje na dat výčtu. Tento atribut je ignorován, pokud neodpovídá vzoru výčtu. Najdete v článku `xs:simpleType` části omezení.|  
|`list`|Podporováno. Mapuje příznak kontrakty dat výčtu. Najdete v článku `xs:simpleType` uvádí oddíl.|  
|`union`|Je zakázané.|  
  
### <a name="xsrestriction"></a>\<xs:restriction>  
  
-   Komplexní typ omezení jsou podporovány pouze pro základní = "`xs:anyType`".  
  
-   Jednoduchý typ omezení u `xs:string` které nemají žádné omezení omezující než `xs:enumeration` jsou namapované na kontrakty dat výčtu.  
  
-   Další omezení jednoduchého typu jsou namapované na typy, které omezují. Například omezení u `xs:int` mapuje na typ integer, stejně jako `xs:int` sám nemá. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] primitivní typ mapování, najdete v části typ nebo primitivní mapování.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`base`|Musí být podporovaná jednoduchého typu nebo `xs:anyType`.|  
|`id`|Ignorovat.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > pro všechny další případy: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Pokud je k dispozici, musí být odvozen z podporovaných primitivního typu.|  
|`minExclusive`|Ignorovat.|  
|`minInclusive`|Ignorovat.|  
|`maxExclusive`|Ignorovat.|  
|`maxInclusive`|Ignorovat.|  
|`totalDigits`|Ignorovat.|  
|`fractionDigits`|Ignorovat.|  
|`length`|Ignorovat.|  
|`minLength`|Ignorovat.|  
|`maxLength`|Ignorovat.|  
|`enumeration`|Ignorovat.|  
|`whiteSpace`|Ignorovat.|  
|`pattern`|Ignorovat.|  
|(prázdný)|Podporováno.|  
  
## <a name="enumeration"></a>Výčet  
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction > pro výčty: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`base`|Pokud existuje, musí být `xs:string`.|  
|`id`|Ignorovat.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > pro výčty: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Pokud je k dispozici, musí být omezení enumeration podporována kontrakt dat (této části).|  
|`minExclusive`|Ignorovat.|  
|`minInclusive`|Ignorovat.|  
|`maxExclusive`|Ignorovat.|  
|`maxInclusive`|Ignorovat.|  
|`totalDigits`|Ignorovat.|  
|`fractionDigits`|Ignorovat.|  
|`length`|Je zakázané.|  
|`minLength`|Je zakázané.|  
|`maxLength`|Je zakázané.|  
|`enumeration`|Podporováno. Je ignorován výčtu "id" a "value" mapuje název hodnoty v kontraktu dat výčtu.|  
|`whiteSpace`|Je zakázané.|  
|`pattern`|Je zakázané.|  
|(prázdný)|Nepodporuje mapuje na typ prázdný výčet.|  
  
 Následující kód ukazuje výčet tříd jazyka C#.  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 }  
  
 Tato třída se mapuje na schéma následující pomocí `DataContractSerializer`. Pokud hodnoty výčtu začínají 1, `xs:annotation` nejsou generované bloky.  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a>\<xs:list>  
 `DataContractSerializer` Výčtové typy mapy označené jako `System.FlagsAttribute` k `xs:list` odvozené z `xs:string`. Žádný jiný `xs:list` rozdíly jsou podporovány.  
  
### <a name="xslist-attributes"></a>\<xs:list >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`itemType`|Je zakázané.|  
|`id`|Ignorovat.|  
  
### <a name="xslist-contents"></a>\<xs:list >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Musí být omezení `xs:string` pomocí `xs:enumeration` omezující vlastnosti.|  
  
 Pokud hodnota výčtu nedodrží druhou mocninou 2 postupu (výchozí nastavení pro příznaky), hodnota je uložena v `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.  
  
 Následující kód například příznaky typ výčtu.  
  
```  
[Flags]  
public enum AuthFlags  
{    
  AuthAnonymous = 1,  
  AuthBasic = 2,  
  AuthNTLM = 4,  
  AuthMD5 = 16,  
  AuthWindowsLiveID = 64,  
}  
```  
  
 Tento typ se mapuje na následující schéma.  
  
```xml  
<xs:simpleType name="AuthFlags">  
    <xs:list>  
      <xs:simpleType>  
        <xs:restriction base="xs:string">  
          <xs:enumeration value="AuthAnonymous" />  
          <xs:enumeration value="AuthBasic" />  
          <xs:enumeration value="AuthNTLM" />  
          <xs:enumeration value="AuthMD5">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a>Dědičnost  
  
### <a name="general-rules"></a>Obecná pravidla  
 Kontrakt dat může dědit vlastnosti z jiné smlouvy data. Tyto smlouvy data namapovat na základní a jsou odvozené typy rozšíření pomocí `<xs:extension>` konstrukce schématu XML.  
  
 Kontrakt dat nemůže Zdědit z kontraktu dat kolekce.  
  
 Například následující kód je kontraktu dat.  
  
```  
[DataContract]  
public class Person  
{  
  [DataMember]  
  public string Name;  
}  
[DataContract]  
public class Employee : Person   
{      
  [DataMember]  
  public int ID;  
}  
```  
  
 Tento kontrakt dat se mapuje na typ deklarace schématu XML.  
  
```xml  
<xs:complexType name="Employee">  
 <xs:complexContent mixed="false">  
  <xs:extension base="tns:Person">  
   <xs:sequence>  
    <xs:element minOccurs="0" name="ID" type="xs:int"/>  
   </xs:sequence>  
  </xs:extension>  
 </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="Person">  
 <xs:sequence>  
  <xs:element minOccurs="0" name="Name"   
    nillable="true" type="xs:string"/>  
 </xs:sequence>  
</xs:complexType>  
```  
  
### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`id`|Ignorovat.|  
|`mixed`|Musí mít hodnotu false.|  
  
### <a name="xscomplexcontent-contents"></a>\<xs:complexContent >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`restriction`|Zakázáno, s výjimkou základní = "`xs:anyType`". K tomu je ekvivalentní umístění obsahu `xs:restriction` přímo v kontejneru systému `xs:complexContent`.|  
|`extension`|Podporováno. Mapuje data smluvním vztahu dědičnosti.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:Extension > v \<xs:complexContent >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`id`|Ignorovat.|  
|`base`|Podporováno. Mapuje kontrakt základní dat zadejte, zda tento typ dědí od.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:Extension > v \<xs:complexContent >: obsah  
 Pravidla jsou stejné jako u `<xs:complexType>` obsah.  
  
 Pokud `<xs:sequence>` je k dispozici, jeho členských elementy mapy členům další data, které se nacházejí v kontraktu odvozené data.  
  
 Pokud odvozený typ obsahuje element se stejným názvem jako element v základním typu, deklaraci duplicitní element se mapuje na člena s názvem, který se vygeneruje být jedinečný. Kladná celá čísla se přidají k názvu data člena ("Člen1", "člen2" a tak dále) až do nalezení jedinečný název. Na druhé straně:  
  
-   Kontrakt odvozené dat má datový člen se stejným názvem a typem jako člena dat v kontraktu základní data `DataContractSerializer` generuje tento odpovídající element v odvozeném typu.  
  
-   Pokud má datový člen se stejným názvem jako člena dat ve kontraktu základní data, ale jiný typ kontraktu odvozené data `DataContractSerializer` importuje schéma s elementem typu `xs:anyType` v základním typu a odvozený typ deklarace. Původní název typu se zachová, i v `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Obě varianty může vést ke schématu s nejednoznačný modelu obsahu, což závisí v řádu příslušné datové členy.  
  
## <a name="typeprimitive-mapping"></a>Typ nebo primitivní mapování  
 `DataContractSerializer` Používá následující mapování pro primitivní typy schématu XML.  
  
|Typ XSD|Typ formátu .NET|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime> a <xref:System.TimeSpan> posunu. Najdete v části serializace DateTimeOffset níže.|  
|`time`|<xref:System.String>.|  
|`date`|<xref:System.String>.|  
|`gYearMonth`|<xref:System.String>.|  
|`gYear`|<xref:System.String>.|  
|`gMonthDay`|<xref:System.String>.|  
|`gDay`|<xref:System.String>.|  
|`gMonth`|<xref:System.String>.|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<xref:System.Byte> Pole.|  
|`hexBinary`|<xref:System.String>.|  
|`float`|<xref:System.Single>.|  
|`double`|<xref:System.Double>.|  
|`anyURI`|<xref:System.Uri>.|  
|`QName`|<xref:System.Xml.XmlQualifiedName>.|  
|`string`|<xref:System.String>.|  
|`normalizedString`|<xref:System.String>.|  
|`token`|<xref:System.String>.|  
|`language`|<xref:System.String>.|  
|`Name`|<xref:System.String>.|  
|`NCName`|<xref:System.String>.|  
|`ID`|<xref:System.String>.|  
|`IDREF`|<xref:System.String>.|  
|`IDREFS`|<xref:System.String>.|  
|`ENTITY`|<xref:System.String>.|  
|`ENTITIES`|<xref:System.String>.|  
|`NMTOKEN`|<xref:System.String>.|  
|`NMTOKENS`|<xref:System.String>.|  
|`decimal`|<xref:System.Decimal>.|  
|`integer`|<xref:System.Int64>.|  
|`nonPositiveInteger`|<xref:System.Int64>.|  
|`negativeInteger`|<xref:System.Int64>.|  
|`long`|<xref:System.Int64>.|  
|`int`|<xref:System.Int32>.|  
|`short`|<xref:System.Int16>.|  
|`Byte`|<xref:System.SByte>.|  
|`nonNegativeInteger`|<xref:System.Int64>.|  
|`unsignedLong`|<xref:System.UInt64>.|  
|`unsignedInt`|<xref:System.UInt32>.|  
|`unsignedShort`|<xref:System.UInt16>.|  
|`unsignedByte`|<xref:System.Byte>.|  
|`positiveInteger`|<xref:System.Int64>.|  
  
## <a name="iserializable-types-mapping"></a>Typy iSerializable mapování  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, `ISerializable` byla zavedena jako obecné mechanismus pro serializaci objektů pro přenos trvalost nebo data. Existuje mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které implementují `ISerializable` , které lze předat mezi aplikacemi. `DataContractSerializer` přirozeně poskytuje podporu pro `ISerializable` třídy. `DataContractSerializer` Mapuje `ISerializable` typy schémat implementace, které liší pouze QName (kvalifikovaný název) typu a jsou efektivně vlastnost kolekce. Například `DataContractSerializer` mapuje <xref:System.Exception> na následující typ XSD v http://schemas.datacontract.org/2004/07/System oboru názvů.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 Volitelný atribut `ser:FactoryType` deklarované v serializaci kontraktu dat schématu odkazuje na třídu objektů factory, který může deserializovat daný typ. Třídu objektů factory musí být součástí kolekce známé typy `DataContractSerializer` instance, používá. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] známé typy, najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>Schéma serializace kontraktu  
 Počet schémata exportované sadou `DataContractSerializer` použijte typy elementů a atributů z speciální obor názvů kontraktu serializace dat:  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 Toto je úplné deklarace schématu serializace dat kontrakt.  
  
```xml  
<xs:schema attributeFormDefault="qualified"          
   elementFormDefault="qualified"        
   targetNamespace =   
    "http://schemas.microsoft.com/2003/10/Serialization/"   
   xmlns:xs="http://www.w3.org/2001/XMLSchema"        
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">  
  
 <!-- Top-level elements for primitive types. -->  
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>  
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>  
 <xs:element name="base64Binary"  
       nillable="true" type="xs:base64Binary"/>  
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>  
 <xs:element name="byte" nillable="true" type="xs:byte"/>  
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>  
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>  
 <xs:element name="double" nillable="true" type="xs:double"/>  
 <xs:element name="float" nillable="true" type="xs:float"/>  
 <xs:element name="int" nillable="true" type="xs:int"/>  
 <xs:element name="long" nillable="true" type="xs:long"/>  
 <xs:element name="QName" nillable="true" type="xs:QName"/>  
 <xs:element name="short" nillable="true" type="xs:short"/>  
 <xs:element name="string" nillable="true" type="xs:string"/>  
 <xs:element name="unsignedByte"  
       nillable="true" type="xs:unsignedByte"/>  
 <xs:element name="unsignedInt"  
       nillable="true" type="xs:unsignedInt"/>  
 <xs:element name="unsignedLong"  
       nillable="true" type="xs:unsignedLong"/>  
 <xs:element name="unsignedShort"  
       nillable="true" type="xs:unsignedShort"/>  
  
 <!-- Primitive types introduced for certain .NET simple types. -->  
 <xs:element name="char" nillable="true" type="tns:char"/>  
 <xs:simpleType name="char">  
  <xs:restriction base="xs:int"/>  
 </xs:simpleType>  
  
 <!-- xs:duration is restricted to an ordered value space,  
    to map to System.TimeSpan -->  
 <xs:element name="duration" nillable="true" type="tns:duration"/>  
 <xs:simpleType name="duration">  
  <xs:restriction base="xs:duration">  
   <xs:pattern   
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>  
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>  
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <xs:element name="guid" nillable="true" type="tns:guid"/>  
 <xs:simpleType name="guid">  
  <xs:restriction base="xs:string">  
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <!-- This is used for schemas exported from ISerializable type. -->  
 <xs:attribute name="FactoryType" type="xs:QName"/>  
</xs:schema>  
```  
  
 Následující potřeba poznamenat:  
  
-   `ser:char` Uvádíme představují znaky znakové sady Unicode typu <xref:System.Char>.  
  
-   `valuespace` z `xs:duration` zkrátila seřazené sady tak, aby bylo možné namapovat na <xref:System.TimeSpan>.  
  
-   `FactoryType` se používá v schémata exportovat z typů, které jsou odvozeny od <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>Import schémata bez kontraktu  
 `DataContractSerializer` má `ImportXmlTypes` možnost, povolíte import schémat, které nejsou v souladu s `DataContractSerializer` profil XSD (najdete v článku <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost). Nastavení této možnosti na `true` umožňuje přijetí nonkonformní typy schémat a jejich mapování pro následující implementaci <xref:System.Xml.Serialization.IXmlSerializable> zabalení pole <xref:System.Xml.XmlNode> (jenom název třídy se liší).  
  
```  
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]  
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]  
public partial class Person : object, IXmlSerializable  
{    
  private XmlNode[] nodesField;    
  private static XmlQualifiedName typeName =   
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");    
  public XmlNode[] Nodes  
  {  
    get {return this.nodesField;}  
    set {this.nodesField = value;}  
  }    
  public void ReadXml(XmlReader reader)  
  {  
    this.nodesField = XmlSerializableServices.ReadNodes(reader);  
  }    
  public void WriteXml(XmlWriter writer)  
  {  
    XmlSerializableServices.WriteNodes(writer, this.Nodes);  
  }    
  public System.Xml.Schema.XmlSchema GetSchema()  
  {  
    return null;  
  }    
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)  
  {  
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);  
    return typeName;  
  }  
}  
```  
  
## <a name="datetimeoffset-serialization"></a>Serializace DateTimeOffset  
 <xref:System.DateTimeOffset> Nepovažuje primitivního typu. Místo toho je serializováno jako element komplexní se skládá ze dvou částí. Představuje první část času a druhá část představuje posun od času. V následujícím kódu je uveden příklad serializovaných DateTimeOffset hodnoty.  
  
```xml  
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">  
  <DateTime i:type="b:dateTime" xmlns=""   
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00    
  </DateTime>   
  <OffsetMinutes i:type="b:short" xmlns=""   
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480  
   </OffsetMinutes>   
</OffSet>  
```  
  
 Schéma je následující.  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
