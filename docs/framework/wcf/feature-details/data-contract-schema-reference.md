---
title: Schéma kontraktů dat – referenční informace
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: a4ddaaea2133a8adf5271628f442644194a7f453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857178"
---
# <a name="data-contract-schema-reference"></a>Schéma kontraktů dat – referenční informace
Toto téma popisuje dílčí sady schématu XML (XSD) používá <xref:System.Runtime.Serialization.DataContractSerializer> k popisu common language runtime (CLR) typy pro serializaci kódu XML.  
  
## <a name="datacontractserializer-mappings"></a>Mapování třídy DataContractSerializer  
 `DataContractSerializer` Mapuje CLR typy XSD, při exportu metadat ze služby Windows Communication Foundation (WCF) pomocí koncových bodů metadat nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Také mapuje XSD na typy CLR při použití Svcutil.exe k přístupu dokumenty služby popis jazyka WSDL (Web) nebo XSD a generovat kontrakty dat pro služby nebo klienty.  
  
 Pouze instance schématu XML, které v souladu s požadavky uvedenými v tomto dokumentu lze mapovat typy CLR pomocí `DataContractSerializer`.  
  
### <a name="support-levels"></a>Úrovně podpory  
 `DataContractSerializer` Pro danou funkci schématu XML obsahuje následující úrovně podpory:  
  
- **Podporované**. Je explicitní mapování z této funkce CLR typy atributů (nebo obojí) pomocí `DataContractSerializer`.  
  
- **Ignorovat**. Tato funkce je povolen ve schématech importované tímto seznamem `DataContractSerializer`, ale nemá žádný vliv na generování kódu.  
  
- **Je zakázané**. `DataContractSerializer` Nepodporuje import schématu pomocí funkce. Například Svcutil.exe při přístupu k souboru WSDL se schématem, který používá funkce, přejde k použití <xref:System.Xml.Serialization.XmlSerializer> místo. Toto je ve výchozím nastavení.  
  
## <a name="general-information"></a>Obecné informace  
  
- Obor názvů schématu je popsán v [schématu XML](https://go.microsoft.com/fwlink/?LinkId=95475). V tomto dokumentu se používá předpona "x".  
  
- Všechny atributy s oborem názvů schéma se ignorují.  
  
- Žádné poznámky (s výjimkou těch popsaných v tomto dokumentu) jsou ignorovány.  
  
### <a name="xsschema-attributes"></a>\<xs:Schema >: atributy  
  
|Atribut|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Ignorovat.|  
|`blockDefault`|Ignorovat.|  
|`elementFormDefault`|Musí být kvalifikovaný. Všechny elementy musí být kvalifikován pro schéma, aby ho podporoval účet `DataContractSerializer`. To můžete provést buď nastavením xs:schema/@elementFormDefault "kvalifikovaný" nebo nastavením xs:element/@form na "kvalifikovaný" na každý jednotlivý element deklarace.|  
|`finalDefault`|Ignorovat.|  
|`Id`|Ignorovat.|  
|`targetNamespace`|Podporované a namapována na obor názvů kontraktu dat. Pokud tento atribut není zadán, použije se prázdný obor názvů. Vyhrazený obor názvů nemůže být `http://schemas.microsoft.com/2003/10/Serialization/`.|  
|`version`|Ignorovat.|  
  
### <a name="xsschema-contents"></a>\<xs:Schema >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`include`|Podporované. `DataContractSerializer` podporuje xs: zahrnují a xs:import. Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje na metadata je načtena z místního souboru. Seznam souborů schématu musí být předán mechanismem out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumentů jsou ignorovány.|  
|`redefine`|Je zakázané. Použití `xs:redefine` takovýto `DataContractSerializer` z bezpečnostních důvodů: `x:redefine` vyžaduje `schemaLocation` postupovat. V některých případech se omezují pomocí kontraktu DataContract Svcutil.exe použití `schemaLocation`.|  
|`import`|Podporované. `DataContractSerializer` podporuje `xs:include` a `xs:import`. Ale Svcutil.exe omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazuje na metadata je načtena z místního souboru. Seznam souborů schématu musí být předán mechanismem out-of-band a ne prostřednictvím `include` v tomto případě; `include`d schématu dokumentů jsou ignorovány.|  
|`simpleType`|Podporované. Zobrazit `xs:simpleType` oddílu.|  
|`complexType`|Podporované, mapuje kontraktů dat Zobrazit `xs:complexType` oddílu.|  
|`group`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nedá odkazovat v rámci `complexType` nebo jiných objektů, které podporované.|  
|`attributeGroup`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nedá odkazovat v rámci `complexType` nebo jiných objektů, které podporované.|  
|`element`|Podporované. Zobrazit globální prvek prohlášení (Připravený).|  
|`attribute`|Ignorovat. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`, a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené objekty `xs:schema`, ale nedá odkazovat v rámci `complexType` nebo jiných objektů, které podporované.|  
|`notation`|Ignorovat.|  
  
## <a name="complex-types--xscomplextype"></a>Komplexní typy – \<xs:complexType >  
  
### <a name="general-information"></a>Obecné informace  
 Každý komplexní typ \<xs:complexType > mapuje data smlouvy.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`abstract`|Musí mít hodnotu false (výchozí).|  
|`block`|Je zakázané.|  
|`final`|Ignorovat.|  
|`id`|Ignorovat.|  
|`mixed`|Musí mít hodnotu false (výchozí).|  
|`name`|Podporované a mapovat na název kontraktu dat. Pokud v názvu tečky, je proveden pokus o mapování typu na typ vnitřní. Například komplexní typ s názvem `A.B` mapuje kontraktu dat. typ, který je vnitřní typ typu s názvem kontraktu dat `A`, ale existuje pouze v případě, že tyto údaje typ kontraktu. Je možné více než jednou úrovní vnoření: například `A.B.C` může být vnitřní typ, ale pouze v případě `A` a `A.B` obě existovat.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleContent`|Rozšíření jsou zakázána.<br /><br /> Omezení je povoleno pouze ze `anySimpleType`.|  
|`complexContent`|Podporované. V tématu "Dědičnost".|  
|`group`|Je zakázané.|  
|`all`|Je zakázané.|  
|`choice`|Zakázáno|  
|`sequence`|Podporované, mapuje se na datové členy kontraktu dat.|  
|`attribute`|Je zakázané, i v případě použití = "prohibited" (s jednou výjimkou). Jsou podporovány pouze volitelné atributy z oboru názvů schématu standardní serializace. Nelze je namapovat na datové členy v kontraktu dat programovacího modelu. V současné době pouze jeden atribut má význam a je popsána v části ISerializable. Případné další se ignorují.|  
|`attributeGroup`|Je zakázané. Ve verzi v1 WCF `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType`.|  
|`anyAttribute`|Je zakázané.|  
|(prázdné)|Mapuje kontraktu dat se žádné datové členy.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:Sequence > komplexní typ: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`id`|Ignorovat.|  
|`maxOccurs`|Musí být 1 (výchozí).|  
|`minOccurs`|Musí být 1 (výchozí).|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:Sequence > komplexní typ: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`element`|Každá instance se mapuje na datový člen.|  
|`group`|Je zakázané.|  
|`choice`|Je zakázané.|  
|`sequence`|Je zakázané.|  
|`any`|Je zakázané.|  
|(prázdné)|Mapuje kontraktu dat se žádné datové členy.|  
  
## <a name="elements--xselement"></a>Elementy – \<xs: element >  
  
### <a name="general-information"></a>Obecné informace  
 `<xs:element>` může dojít v následujících kontextů:  
  
- Může dojít v rámci `<xs:sequence>`, která popisuje datový člen kontraktu běžných dat (bez kolekce). V takovém případě `maxOccurs` atribut musí být 1. (Není povolena hodnota 0).  
  
- Může dojít v rámci `<xs:sequence>`, která popisuje datový člen třídy kontraktu dat kolekce. V takovém případě `maxOccurs` atribut musí být větší než 1 nebo "bez vazby".  
  
- Může dojít v rámci `<xs:schema>` jako globální prvek prohlášení (Připravený).  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs: element > s maxOccurs = 1 v rámci \<xs:sequence > (datové členy)  
  
|Atribut|Schéma|  
|---------------|------------|  
|`ref`|Je zakázané.|  
|`name`|Podporované, mapuje se na názvem datového členu.|  
|`type`|Podporované, mapuje se na datový člen typu. Další informace najdete v tématu typ nebo primitivní mapování. Pokud není zadané (a element neobsahuje anonymního typu), `xs:anyType` se předpokládá, že.|  
|`block`|Ignorovat.|  
|`default`|Je zakázané.|  
|`fixed`|Je zakázané.|  
|`form`|Musí být kvalifikovaný. Tento atribut lze nastavit pomocí `elementFormDefault` na `xs:schema`.|  
|`id`|Ignorovat.|  
|`maxOccurs`|1|  
|`minOccurs`|Mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost datového členu (`IsRequired` platí v případě `minOccurs` 1).|  
|`nillable`|Mapování typu ovlivňuje. Podívejte se na typ nebo primitivní mapování.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs: element > s maxOccurs > 1 v rámci \<xs:sequence > (kolekce)  
  
- Mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
- V kolekci typů je povolen pouze jeden xs: element v rámci xs:sequence.  
  
 Kolekce může být z následujících typů:  
  
- Kolekce pravidelně (například pole).  
  
- Kolekce slovníku (mapování jednu hodnotu; například <xref:System.Collections.Hashtable>).  
  
- Jediným rozdílem mezi slovník a pole typu dvojice klíč/hodnota je vygenerovaný programovacím modelu. Je mechanismus anotace schématu, která slouží k označení, že je daný typ kolekce slovníku.  
  
 Pravidla pro `ref`, `block`, `default`, `fixed`, `form`, a `id` atributy jsou stejné jako u případ jiné kolekce. Ostatní atributy zahrnout v následující tabulce.  
  
|Atribut|Schéma|  
|---------------|------------|  
|`name`|Podporované, mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost v `CollectionDataContractAttribute` atribut.|  
|`type`|Podporované, mapuje se na typ uložený v kolekci.|  
|`maxOccurs`|Větší než 1 nebo "bez vazby". Schéma řadiče domény by měl používat "bez vazby".|  
|`minOccurs`|Ignorovat.|  
|`nillable`|Mapování typu ovlivňuje. Tento atribut se ignoruje pro kolekce slovníku.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs: element > v rámci \<xs:schema > globální deklaraci elementu  
  
- Globální prvek prohlášení (Připravený), který má stejný název a obor názvů jako typ ve schématu nebo, který definuje anonymního typu uvnitř samotného, se říká, že má být přidružena k typu.  
  
- Export schématu: přidružené GEDs jsou generovány pro každý generovaný typ jednoduché i složité.  
  
- Serializace/deserializace: přidružené GEDs se používají jako kořenových elementů typu.  
  
- Import schématu: přidružené GEDs se nevyžadují a jsou ignorovány, pokud, podle následujících pravidel (Pokud definují typy).  
  
|Atribut|Schéma|  
|---------------|------------|  
|`abstract`|Musí mít hodnotu false pro přidružené GEDs.|  
|`block`|Je zakázané v přidružené GEDs.|  
|`default`|Je zakázané v přidružené GEDs.|  
|`final`|Musí mít hodnotu false pro přidružené GEDs.|  
|`fixed`|Je zakázané v přidružené GEDs.|  
|`id`|Ignorovat.|  
|`name`|Podporované. Viz definice přidružené GEDs.|  
|`nillable`|Musí mít hodnotu true pro přidružené GEDs.|  
|`substitutionGroup`|Je zakázané v přidružené GEDs.|  
|`type`|Podporované a musí odpovídat přidruženého typu přidružené GEDs (pokud element obsahuje anonymního typu).|  
  
### <a name="xselement-contents"></a>\<xs: element >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Ignorovat.|  
|`key`|Ignorovat.|  
|`keyref`|Ignorovat.|  
|(prázdné)|Podporované.|  
  
 \* Při použití `simpleType` a `complexType,` mapování pro anonymní typy je stejná jako anonymní typy, s tím rozdílem, že neexistuje žádná kontrakty anonymní data, takže vytvoření kontraktu s názvem dat s názvem odvozen z názvu elementu. Pravidla pro anonymní typy jsou v následujícím seznamu:  
  
- Podrobnosti implementace WCF: Pokud `xs:element` název neobsahuje období, anonymního typu se mapuje na vnitřní typ vnější datový typ kontraktu. Pokud název obsahuje tečky, je výsledný typ kontraktu dat nezávislé (ne vnitřní typ).  
  
- Název kontraktu generovaná data vnitřního typu je názvem kontraktu dat z vnějšího typu následovaných tečkou, název elementu a řetězce "Type".  
  
- Pokud dat smluvním vztahu se stejným názvem už existuje, název je jedinečný připojením "1", "2", "3", a tak dále, dokud se vytvoří jedinečný název.  
  
## <a name="simple-types---xssimpletype"></a>Jednoduché typy – \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`final`|Ignorovat.|  
|`id`|Ignorovat.|  
|`name`|Podporované, mapuje se na data název kontraktu.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`restriction`|Podporované. Mapuje kontraktů dat výčtu. Tento atribut se ignoruje, pokud neodpovídá vzoru výčtu. Zobrazit `xs:simpleType` omezení.|  
|`list`|Podporované. Mapuje k nastavení příznaku kontraktů dat výčtu. Zobrazit `xs:simpleType` uvádí oddíl.|  
|`union`|Je zakázané.|  
  
### <a name="xsrestriction"></a>\<xs:restriction >  
  
- Komplexní typ omezení jsou podporovány pouze pro základ = "`xs:anyType`".  
  
- Omezení jednoduchého typu `xs:string` , které nemají žádné omezení omezující vlastnosti jiné než `xs:enumeration` se mapují na výčet data smlouvy.  
  
- Další omezení jednoduchého typu jsou mapovány na typy, které omezují. Například omezení `xs:int` mapuje na celé číslo, stejně jako `xs:int` sám nemá. Další informace o mapování primitivní typ naleznete v tématu typ nebo primitivní mapování.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`base`|Musí být jednoduchý typ. podporované nebo `xs:anyType`.|  
|`id`|Ignorovat.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > pro všechny ostatní případy: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Pokud jsou k dispozici, musí být odvozen od podporovaným primitivním typem.|  
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
|(prázdné)|Podporované.|  
  
## <a name="enumeration"></a>Výčet  
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction > pro výčty: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`base`|Pokud jsou k dispozici, musí být `xs:string`.|  
|`id`|Ignorovat.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > pro výčty: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Pokud jsou k dispozici, musí být omezení enumeration podporována kontraktu dat. (v této části).|  
|`minExclusive`|Ignorovat.|  
|`minInclusive`|Ignorovat.|  
|`maxExclusive`|Ignorovat.|  
|`maxInclusive`|Ignorovat.|  
|`totalDigits`|Ignorovat.|  
|`fractionDigits`|Ignorovat.|  
|`length`|Je zakázané.|  
|`minLength`|Je zakázané.|  
|`maxLength`|Je zakázané.|  
|`enumeration`|Podporované. Ignoruje výčet "id" a "value" mapuje na název hodnoty v kontraktu dat výčtu.|  
|`whiteSpace`|Je zakázané.|  
|`pattern`|Je zakázané.|  
|(prázdné)|Podporované, mapuje se na typ prázdný výčet.|  
  
 Následující kód ukazuje výčet tříd jazyka C#.  
  
```csharp  
public enum MyEnum  
{  
  first = 3,  
  second = 4,  
  third =5  
}  
```  
  
 Tato třída se mapuje na následující schéma podle `DataContractSerializer`. Pokud hodnoty výčtu spustit z 1, `xs:annotation` bloky se negenerují.  
  
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
 `DataContractSerializer` mapy výčtové typy označené `System.FlagsAttribute` k `xs:list` odvozený od `xs:string`. Žádné jiné `xs:list` variace se podporují.  
  
### <a name="xslist-attributes"></a>\<xs:list >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`itemType`|Je zakázané.|  
|`id`|Ignorovat.|  
  
### <a name="xslist-contents"></a>\<xs:list >: obsah  
  
|Obsah|Schéma|  
|--------------|------------|  
|`simpleType`|Musí být omezení z `xs:string` pomocí `xs:enumeration` omezující vlastnost.|  
  
 Pokud hodnota výčtu nedodrží mocninou čísla 2 průběh (výchozí nastavení pro příznaky), hodnota je uložena v `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.  
  
 Následující kód například příznaky typu výčtu.  
  
```csharp  
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
  
 Tento typ se mapuje na následujícím schématu.  
  
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
  
### <a name="general-rules"></a>Obecná pravidla.  
 Kontrakt dat může dědit z jiné smlouvy data. Tyto smlouvy dat namapovat na bázi a jsou odvozené typy rozšíření pomocí `<xs:extension>` konstrukce schématu XML.  
  
 Kontrakt dat nemůže dědit z kontraktu dat kolekce.  
  
 Například následující kód je datový kontrakt.  
  
```csharp  
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
  
 Tento kontrakt dat mapuje následující deklarace typu schématu XML.  
  
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
|`restriction`|Je zakázané, kromě případů, kdy je to základní = "`xs:anyType`". Je ekvivalentní k umístění obsahu `xs:restriction` přímo pod kontejnerem `xs:complexContent`.|  
|`extension`|Podporované. Mapuje na Dědičnost kontraktů dat|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:Extension > v \<xs:complexContent >: atributy  
  
|Atribut|Schéma|  
|---------------|------------|  
|`id`|Ignorovat.|  
|`base`|Podporované. Mapuje se na základní datový kontrakt zadejte, že tento typ dědí z.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:Extension > v \<xs:complexContent >: obsah  
 Pravidla jsou stejné jako v případě `<xs:complexType>` obsah.  
  
 Pokud `<xs:sequence>` je k dispozici, její člen prvky namapovat na další datové členy, které se nacházejí v kontraktu odvozené údaje.  
  
 Pokud odvozený typ obsahuje element se stejným názvem jako prvek v základním typu, deklarace duplicitní prvek mapuje na datový člen s názvem, který je generován být jedinečný. Kladná celá čísla jsou přidány do názvem datového členu ("member1", "člen2" a tak dále) dokud nebude nalezen jedinečný název. Naopak:  
  
- Pokud kontrakt odvozené dat má datový člen se stejným názvem a typem jako datový člen základní datový kontrakt, `DataContractSerializer` generuje tento odpovídající element v odvozeném typu.  
  
- Pokud kontrakt odvozené dat má datový člen se stejným názvem jako datový člen v základní datový kontrakt ale odlišným typem, `DataContractSerializer` importuje schéma s elementem typu `xs:anyType` v základním typu a deklarace odvozených typů. Původní název typu je zachováno v `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Obě varianty může vést k schéma s nejednoznačný obsahu modelu, který závisí v řádu příslušné datové členy.  
  
## <a name="typeprimitive-mapping"></a>Typ nebo primitivní mapování  
 `DataContractSerializer` Používá následující mapování pro primitivní typy schématu XML.  
  
|Typ XSD|Typ formátu .NET|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime> a <xref:System.TimeSpan> posunu. Podívejte se níže DateTimeOffset serializace.|  
|`time`|<xref:System.String>.|  
|`date`|<xref:System.String>.|  
|`gYearMonth`|<xref:System.String>.|  
|`gYear`|<xref:System.String>.|  
|`gMonthDay`|<xref:System.String>.|  
|`gDay`|<xref:System.String>.|  
|`gMonth`|<xref:System.String>.|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<xref:System.Byte> pole.|  
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
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verze 1.0, <xref:System.Runtime.Serialization.ISerializable> byla zavedená jako obecný mechanismus k serializaci objektů pro přenos trvalého nebo data. Existuje několik instancí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které implementují `ISerializable` a, které mohou být předány mezi aplikacemi. <xref:System.Runtime.Serialization.DataContractSerializer> přirozeně poskytuje podporu pro `ISerializable` třídy. `DataContractSerializer` Mapuje `ISerializable` implementace schématu typy, které se liší pouze podle typu QName (úplný název) a jsou kolekce vlastností. Například `DataContractSerializer` mapuje <xref:System.Exception> pro následující typ XSD v `http://schemas.datacontract.org/2004/07/System` oboru názvů.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 Volitelný atribut `ser:FactoryType` deklarované v serializaci smlouvy dat schématu odkazuje na třídu objektů factory, který může deserializovat daný typ. Objekt pro vytváření tříd musí být součástí kolekce známých typů ve `DataContractSerializer` instance, používá. Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>Schéma serializace pomocí kontraktu DataContract  
 Počet schémata exportované sadou `DataContractSerializer` používat typy, elementů a atributů z oboru názvů zvláštní serializaci smlouvy dat:  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 Toto je úplnou deklaraci schématu serializaci dat smlouvy.  
  
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
  
 Následující by měl být jste si poznamenali:  
  
- `ser:char` se používá k reprezentaci znaků Unicode typu <xref:System.Char>.  
  
- `valuespace` z `xs:duration` byla snížena na seřazené sady, takže je možné mapovat na <xref:System.TimeSpan>.  
  
- `FactoryType` se používá ve schématech exportovat z typů, které jsou odvozeny z <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>Import jiné než DataContract schémata  
 `DataContractSerializer` má `ImportXmlTypes` možnost, povolíte import schémat, které není v souladu s `DataContractSerializer` XSD profilu (najdete v článku <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost). Tuto volbu nastavíte `true` povoluje přijetí nonkonformní schématu typy a mapování pro následující implementaci <xref:System.Xml.Serialization.IXmlSerializable> obtékání pole <xref:System.Xml.XmlNode> (se liší jenom název třídy).  
  
```csharp  
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
 <xref:System.DateTimeOffset> Není považován za primitivního typu. Místo toho je serializován jako komplexních prvků se skládá ze dvou částí. První část představuje datum čas a druhá část představuje posun od času. Příklad serializovaná hodnota DateTimeOffset je znázorněno v následujícím kódu.  
  
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
  
 Schéma je následujícím způsobem.  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:element name="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
