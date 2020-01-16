---
title: Schéma kontraktů dat – referenční informace
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963373"
---
# <a name="data-contract-schema-reference"></a>Schéma kontraktů dat – referenční informace

Toto téma popisuje podmnožinu schématu XML (XSD) používaného <xref:System.Runtime.Serialization.DataContractSerializer> k popisu typů modulu CLR (Common Language Runtime) pro serializaci XML.

## <a name="datacontractserializer-mappings"></a>Mapování DataContractSerializer

`DataContractSerializer` mapuje typy CLR na XSD, pokud jsou metadata exportována ze služby Windows Communication Foundation (WCF) pomocí koncového bodu metadat nebo [Nástroje pro tvorbu metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).

`DataContractSerializer` také mapuje XSD na typy CLR, pokud se Svcutil. exe používá pro přístup k dokumentům WSDL (Web Services Description Language) nebo XSD a k vygenerování kontraktů dat pro služby nebo klienty.

Pouze instance schématu XML, které odpovídají požadavkům uvedeným v tomto dokumentu, lze namapovat na typy CLR pomocí `DataContractSerializer`.

### <a name="support-levels"></a>Úrovně podpory

`DataContractSerializer` poskytuje následující úrovně podpory pro danou funkci schématu XML:

- **Podporuje**se. Existuje explicitní mapování z této funkce na typy CLR nebo atributy (nebo obojí) pomocí `DataContractSerializer`.

- **Ignoruje**se. Tato funkce je povolena v schématech importovaných `DataContractSerializer`, ale nemá žádný vliv na generování kódu.

- **Zakázané**. `DataContractSerializer` nepodporuje import schématu pomocí funkce. Například Svcutil. exe při přístupu k WSDL se schématem, které tuto funkci používá, se místo toho vrátí k použití <xref:System.Xml.Serialization.XmlSerializer>. Toto je ve výchozím nastavení.

## <a name="general-information"></a>Obecné informace

- Obor názvů schématu je popsán ve [schématu XML](https://www.w3.org/2001/XMLSchema). V tomto dokumentu je použita předpona "XS".

- Všechny atributy s oborem názvů bez schématu jsou ignorovány.

- Jakékoli poznámky (kromě těch, které jsou popsány v tomto dokumentu) se ignorují.

### <a name="xsschema-attributes"></a>\<xs: Schema >: atributy

|Atribut|Kontraktu DataContract|
|---------------|------------------|
|`attributeFormDefault`|Přeskočen.|
|`blockDefault`|Přeskočen.|
|`elementFormDefault`|Musí být kvalifikován. Všechny elementy musí být kvalifikovány, aby bylo schéma podporováno nástrojem `DataContractSerializer`. To lze provést buď nastavením xs:schema/@elementFormDefault na "kvalifikovaný", nebo nastavením xs:element/@form na "kvalifikovaný" pro každou deklaraci jednotlivých prvků.|
|`finalDefault`|Přeskočen.|
|`Id`|Přeskočen.|
|`targetNamespace`|Podporováno a mapováno na obor názvů kontraktu dat. Pokud tento atribut není zadán, je použit prázdný obor názvů. Nemůže se jednat o vyhrazený obor názvů `http://schemas.microsoft.com/2003/10/Serialization/`.|
|`version`|Přeskočen.|

### <a name="xsschema-contents"></a>\<xs: > schématu: obsah

|Obsah|Schéma|
|--------------|------------|
|`include`|Podporováno. `DataContractSerializer` podporuje xs: include a xs: import. Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazů, pokud jsou metadata načtena z místního souboru. Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. dokumenty schématu `include`d jsou ignorovány.|
|`redefine`|Zakázán. Z důvodů zabezpečení je použití `xs:redefine` zakázáno `DataContractSerializer`: `x:redefine` vyžaduje, aby byly dodrženy `schemaLocation`. Za určitých okolností Svcutil. exe využívající DataContract omezuje použití `schemaLocation`.|
|`import`|Podporováno. `DataContractSerializer` podporuje `xs:include` a `xs:import`. Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazů, pokud jsou metadata načtena z místního souboru. Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. dokumenty schématu `include`d jsou ignorovány.|
|`simpleType`|Podporováno. Viz část `xs:simpleType`.|
|`complexType`|Podporováno, mapuje se na kontrakty dat. Viz část `xs:complexType`.|
|`group`|Přeskočen. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené položky `xs:schema`, ale nelze je odkazovat v rámci `complexType` nebo jiné podporované konstrukce.|
|`attributeGroup`|Přeskočen. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené položky `xs:schema`, ale nelze je odkazovat v rámci `complexType` nebo jiné podporované konstrukce.|
|`element`|Podporováno. Viz deklarace globálních elementů (připravený).|
|`attribute`|Přeskočen. `DataContractSerializer` nepodporuje použití `xs:group`, `xs:attributeGroup`a `xs:attribute`. Tyto deklarace jsou ignorovány jako podřízené položky `xs:schema`, ale nelze je odkazovat v rámci `complexType` nebo jiné podporované konstrukce.|
|`notation`|Přeskočen.|

## <a name="complex-types--xscomplextype"></a>Komplexní typy – \<xs: complexType >

### <a name="general-information"></a>Obecné informace

Každý komplexní typ \<xs: complexType > mapuje na kontrakt dat.

### <a name="xscomplextype-attributes"></a>\<xs: complexType >: atributy

|Atribut|Schéma|
|---------------|------------|
|`abstract`|Hodnota musí být false (výchozí).|
|`block`|Zakázán.|
|`final`|Přeskočen.|
|`id`|Přeskočen.|
|`mixed`|Hodnota musí být false (výchozí).|
|`name`|Podporováno a mapováno na název kontraktu dat. Pokud v názvu existují tečky, je proveden pokus o mapování typu na vnitřní typ. Například komplexní typ s názvem `A.B` mapován na typ kontraktu dat, který je vnitřní typ typu s názvem kontraktu dat `A`, ale pouze v případě, že takový typ kontraktu dat existuje. Je možné použít více než jednu úroveň vnoření: `A.B.C` například může být vnitřní typ, ale pouze pokud existují `A` a `A.B` obojí.|

### <a name="xscomplextype-contents"></a>\<xs: complexType >: Contents

|Obsah|Schéma|
|--------------|------------|
|`simpleContent`|Rozšíření jsou zakázána.<br /><br /> Omezení je povoleno pouze z `anySimpleType`.|
|`complexContent`|Podporováno. Viz "dědičnost".|
|`group`|Zakázán.|
|`all`|Zakázán.|
|`choice`|Zakázáno|
|`sequence`|Podporováno, mapuje se na datové členy kontraktu dat.|
|`attribute`|Zakázáno, i když use = "zakázáno" (s jednou výjimkou). Jsou podporovány pouze volitelné atributy z oboru názvů schématu standardní serializace. Nemapují se na datové členy v programovacím modelu kontraktu dat. V současné době pouze jeden takový atribut má význam a je popsán v oddílu ISerializable. Všechny ostatní jsou ignorovány.|
|`attributeGroup`|Zakázán. Ve verzi WCF v1 `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType`.|
|`anyAttribute`|Zakázán.|
|obsahovat|Mapuje se na kontrakt dat bez datových členů.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs: > sekvencí ve komplexním typu: atributy

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`maxOccurs`|Musí mít hodnotu 1 (výchozí).|
|`minOccurs`|Musí mít hodnotu 1 (výchozí).|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs: > sekvencí v komplexním typu: Contents

|Obsah|Schéma|
|--------------|------------|
|`element`|Každá instance se mapuje na datový člen.|
|`group`|Zakázán.|
|`choice`|Zakázán.|
|`sequence`|Zakázán.|
|`any`|Zakázán.|
|obsahovat|Mapuje se na kontrakt dat bez datových členů.|

## <a name="elements--xselement"></a>Elementy – \<xs: element >

### <a name="general-information"></a>Obecné informace

`<xs:element>` může nastat v následujících kontextech:

- Může se vyskytnout v rámci `<xs:sequence>`, který popisuje datový člen běžné (nesběrně) kontraktu dat. V takovém případě musí být atribut `maxOccurs` 1. (Hodnota 0 není povolená).

- Může k tomu dojít v rámci `<xs:sequence>`, která popisuje datový člen kontraktu dat kolekce. V takovém případě musí být atribut `maxOccurs` větší než 1 nebo "Unbounded".

- Může k tomu dojít v rámci `<xs:schema>` jako deklarace globálních elementů (připravený).

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs: element > s hodnota atributu maxOccurs = 1 v \<xs: Sequence > (datové členy).

|Atribut|Schéma|
|---------------|------------|
|`ref`|Zakázán.|
|`name`|Podporováno, mapuje se na název datového členu.|
|`type`|Podporováno, je mapováno na typ datového člena. Další informace naleznete v tématu mapování typů a primitivních hodnot. Pokud není zadán (a prvek neobsahuje anonymní typ), předpokládá se `xs:anyType`.|
|`block`|Přeskočen.|
|`default`|Zakázán.|
|`fixed`|Zakázán.|
|`form`|Musí být kvalifikován. Tento atribut lze nastavit prostřednictvím `elementFormDefault` v `xs:schema`.|
|`id`|Přeskočen.|
|`maxOccurs`|1|
|`minOccurs`|Mapuje se na vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> datového členu (`IsRequired` má hodnotu true, pokud je `minOccurs` 1).|
|`nillable`|Má vliv na mapování typů. Viz mapování typů a primitivních hodnot.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs: element > s maxOccurs > 1 v \<xs: Sequence > (Collections)

- Provede mapování na <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.

- V typech kolekcí je povolena pouze jedna xs: element v rámci typu xs: Sequence.

 Kolekce mohou mít následující typy:

- Běžné kolekce (například pole).

- Kolekce slovníku (mapování jedné hodnoty na jinou, například <xref:System.Collections.Hashtable>).

- Jediný rozdíl mezi slovníkem a polem typu dvojice klíč/hodnota je ve vygenerovaném programovacím modelu. Existuje mechanismus pro anotaci schématu, který lze použít k označení toho, že daný typ je kolekce slovníku.

Pravidla pro atributy `ref`, `block`, `default`, `fixed`, `form`a `id` jsou stejná jako pro případ, kdy není kolekce. Další atributy jsou obsaženy v následující tabulce.

|Atribut|Schéma|
|---------------|------------|
|`name`|Podporováno, mapuje na vlastnost <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> v atributu `CollectionDataContractAttribute`.|
|`type`|Podporováno, mapuje na typ uložený v kolekci.|
|`maxOccurs`|Je větší než 1 nebo "Unbounded". Schéma DC by mělo používat "Unbounded".|
|`minOccurs`|Přeskočen.|
|`nillable`|Má vliv na mapování typů. Tento atribut se pro kolekce slovníku ignoruje.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs: element > v rámci deklarace \<xs: Schema > Global element.

- Deklarace globálních elementů (připravený), která má stejný název a obor názvů jako typ ve schématu nebo který definuje anonymní typ uvnitř sebe sama, je označována jako přidružená k typu.

- Export schématu: přidružená GEDs jsou generována pro každý generovaný typ, jednoduchý i složitý.

- Deserializace/serializace: přidružená GEDs jsou použita jako kořenové prvky pro daný typ.

- Import schématu: přidružené GEDs nejsou povinné a jsou ignorovány, pokud následují následující pravidla (Pokud nedefinují typy).

|Atribut|Schéma|
|---------------|------------|
|`abstract`|Pro přidruženou GEDs musí mít hodnotu false.|
|`block`|Zakázáno v přidružených GEDs.|
|`default`|Zakázáno v přidružených GEDs.|
|`final`|Pro přidruženou GEDs musí mít hodnotu false.|
|`fixed`|Zakázáno v přidružených GEDs.|
|`id`|Přeskočen.|
|`name`|Podporováno. Viz definice přidružených GEDs.|
|`nillable`|Pro přidruženou GEDs musí mít hodnotu true.|
|`substitutionGroup`|Zakázáno v přidružených GEDs.|
|`type`|Podporováno a musí odpovídat přidruženému typu pro přidružené GEDs (Pokud element neobsahuje anonymní typ).|

### <a name="xselement-contents"></a>\<xs: element >: Contents

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Podporováno. *|
|`complexType`|Podporováno. *|
|`unique`|Přeskočen.|
|`key`|Přeskočen.|
|`keyref`|Přeskočen.|
|(prázdné)|Podporováno.|

Při použití `simpleType` a `complexType,` mapování pro anonymní typy je stejný jako u neanonymních typů s tím rozdílem, že neexistují žádné anonymní kontrakty dat, a proto se vytvoří pojmenovaný kontrakt dat s vygenerovaným názvem odvozeným z názvu elementu. \* Pravidla pro anonymní typy jsou v následujícím seznamu:

- Podrobnosti implementace WCF: Pokud název `xs:element` neobsahuje tečky, anonymní typ se mapuje na vnitřní typ typu kontraktu vnějšího data. Pokud název obsahuje tečky, je výsledný typ kontraktu dat nezávislý (nejedná se o vnitřní typ).

- Název kontraktu generovaných dat vnitřního typu je název kontraktu dat vnějšího typu následovaný tečkou, názvem elementu a řetězcem "typ".

- Pokud již existuje kontrakt dat s tímto názvem, je název jedinečný připojením "1", "2", "3" a tak dále, dokud nebude vytvořen jedinečný název.

## <a name="simple-types---xssimpletype"></a>Jednoduché typy – \<xs: simpleType >

### <a name="xssimpletype-attributes"></a>\<xs: simpleType >: atributy

|Atribut|Schéma|
|---------------|------------|
|`final`|Přeskočen.|
|`id`|Přeskočen.|
|`name`|Podporováno, mapuje se na název kontraktu dat.|

### <a name="xssimpletype-contents"></a>\<xs: simpleType >: Contents

|Obsah|Schéma|
|--------------|------------|
|`restriction`|Podporováno. Mapuje se na kontrakty dat výčtu. Tento atribut je ignorován, pokud neodpovídá vzoru výčtu. Viz část omezení `xs:simpleType`.|
|`list`|Podporováno. Provede mapování na označení kontraktů dat výčtu. Přečtěte si část `xs:simpleType` seznamy.|
|`union`|Zakázán.|

### <a name="xsrestriction"></a>\<xs: omezení >

- Omezení komplexního typu jsou podporována pouze pro základní = "`xs:anyType`".

- Jednoduchá omezení typu `xs:string`, která nemají žádné omezující vlastnosti omezení jiné než `xs:enumeration` jsou namapovány na kontrakty dat výčtu.

- Všechna ostatní omezení jednoduchých typů jsou namapována na typy, které omezují. Například omezení `xs:int` se mapuje na celé číslo, stejně jako `xs:int` sám. Další informace o mapování primitivního typu najdete v tématu mapování typů a primitivních typů.

### <a name="xsrestriction-attributes"></a>\<xs: > omezení: atributy

|Atribut|Schéma|
|---------------|------------|
|`base`|Musí být podporovaný jednoduchý typ nebo `xs:anyType`.|
|`id`|Přeskočen.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs: > omezení pro všechny ostatní případy: obsah

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Je-li k dispozici, musí být odvozena z podporovaného primitivního typu.|
|`minExclusive`|Přeskočen.|
|`minInclusive`|Přeskočen.|
|`maxExclusive`|Přeskočen.|
|`maxInclusive`|Přeskočen.|
|`totalDigits`|Přeskočen.|
|`fractionDigits`|Přeskočen.|
|`length`|Přeskočen.|
|`minLength`|Přeskočen.|
|`maxLength`|Přeskočen.|
|`enumeration`|Přeskočen.|
|`whiteSpace`|Přeskočen.|
|`pattern`|Přeskočen.|
|(prázdné)|Podporováno.|

## <a name="enumeration"></a>Výčet

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs: > omezení pro výčty: atributy

|Atribut|Schéma|
|---------------|------------|
|`base`|Je-li k dispozici, musí být `xs:string`.|
|`id`|Přeskočen.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs: omezení > pro výčty: obsah

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Je-li k dispozici, musí se jednat o omezení výčtu podporované kontraktem dat (v této části).|
|`minExclusive`|Přeskočen.|
|`minInclusive`|Přeskočen.|
|`maxExclusive`|Přeskočen.|
|`maxInclusive`|Přeskočen.|
|`totalDigits`|Přeskočen.|
|`fractionDigits`|Přeskočen.|
|`length`|Zakázán.|
|`minLength`|Zakázán.|
|`maxLength`|Zakázán.|
|`enumeration`|Podporováno. Výčet "ID" se ignoruje a hodnota "value" se mapuje na název hodnoty ve kontraktu dat výčtu.|
|`whiteSpace`|Zakázán.|
|`pattern`|Zakázán.|
|obsahovat|Podporováno, mapuje se na prázdný typ výčtu.|

 Následující kód ukazuje třídu C# výčtu.

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

Tato třída se mapuje na následující schéma `DataContractSerializer`. Pokud hodnoty výčtu začínají 1, `xs:annotation` bloky se nevygenerují.

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a>\<xs:list>

`DataContractSerializer` mapuje výčtové typy označené `System.FlagsAttribute` na `xs:list` odvozené od `xs:string`. Nepodporují se žádné jiné varianty `xs:list`.

### <a name="xslist-attributes"></a>\<xs: list >: atributy

|Atribut|Schéma|
|---------------|------------|
|`itemType`|Zakázán.|
|`id`|Přeskočen.|

### <a name="xslist-contents"></a>\<xs: list >: Contents

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Musí být omezení od `xs:string` pomocí omezující vlastnosti `xs:enumeration`.|

Pokud hodnota výčtu nedodržuje mocninu 2 (výchozí pro příznaky), hodnota je uložena v prvku `xs:annotation/xs:appInfo/ser:EnumerationValue`.

Například následující kód označuje typ výčtu.

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

Tento typ se mapuje k následujícímu schématu.

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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
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

Kontrakt dat může dědit od jiného kontraktu dat. Tyto kontrakty dat jsou mapovány na základ a jsou odvozeny pomocí typů rozšíření pomocí `<xs:extension>` konstrukce XML schématu.

Kontrakt dat nemůže dědit od kontraktu dat kolekce.

Například následující kód je kontraktem dat.

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

Tato kontrakt dat se mapuje na následující deklaraci typu schématu XML.

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

### <a name="xscomplexcontent-attributes"></a>\<xs: complexContent >: atributy

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`mixed`|Hodnota musí být false.|

### <a name="xscomplexcontent-contents"></a>\<xs: complexContent >: Contents

|Obsah|Schéma|
|--------------|------------|
|`restriction`|Zakázáno, s výjimkou případů, kdy je Base = "`xs:anyType`". Druhý je ekvivalentní umístění obsahu `xs:restriction` přímo pod kontejnerem `xs:complexContent`.|
|`extension`|Podporováno. Provede mapování na dědičnost kontraktu dat.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs: > rozšíření v \<xs: complexContent >: Attributes

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`base`|Podporováno. Provede mapování základního typu kontraktu dat, z něhož tento typ dědí.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs: > rozšíření v \<xs: complexContent >: Contents

Pravidla jsou stejná jako u `<xs:complexType>` obsahu.

Pokud je k dispozici `<xs:sequence>`, jejich členské prvky se mapují na další datové členy, které jsou přítomny v odvozeném kontraktu dat.

Pokud odvozený typ obsahuje element se stejným názvem jako element v základním typu, je deklarace duplicitních prvků mapována na datový člen s názvem, který je vygenerován jako jedinečný. Kladné celočíselná čísla jsou přidána do názvu datového členu ("Člen1", "member2" atd.), dokud nebude nalezen jedinečný název. Naopak

- Pokud má odvozená kontrakt dat datový člen se stejným názvem a typem jako datový člen v základní kontraktu dat, `DataContractSerializer` generuje tento odpovídající prvek v odvozeném typu.

- Pokud má odvozená kontrakt dat datový člen se stejným názvem jako datový člen v základní kontraktu dat, ale jiný typ, `DataContractSerializer` importuje schéma s prvkem typu `xs:anyType` v obou základních typech i v deklaracích odvozeného typu. Původní název typu se zachová v `xs:annotations/xs:appInfo/ser:ActualType/@Name`.

Obě varianty mohou vést ke schématu s nejednoznačným obsahem modelu, který závisí na pořadí příslušných datových členů.

## <a name="typeprimitive-mapping"></a>Mapování typů a primitivních hodnot

`DataContractSerializer` používá následující mapování pro primitivní typy schémat XML.

|Typ XSD|Typ .NET|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|<xref:System.DateTime> a <xref:System.TimeSpan> pro posun. Viz serializace DateTimeOffset níže.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|pole <xref:System.Byte>.|
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

## <a name="iserializable-types-mapping"></a>Mapování typů ISerializable

V .NET Framework verze 1,0 byla <xref:System.Runtime.Serialization.ISerializable> zavedena jako obecný mechanismus pro serializaci objektů pro trvalost nebo přenos dat. Existuje mnoho typů .NET Framework, které implementují `ISerializable` a které je možné předat mezi aplikacemi. <xref:System.Runtime.Serialization.DataContractSerializer> přirozeně poskytuje podporu pro `ISerializable` třídy. Mapování `DataContractSerializer` `ISerializable` implementují typy schémat, které se liší pouze atributem QName (kvalifikovaného názvu) typu a jsou účinné kolekce vlastností. Například mapování `DataContractSerializer` <xref:System.Exception> k následujícímu typu XSD v oboru názvů `http://schemas.datacontract.org/2004/07/System`.

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

Volitelný atribut `ser:FactoryType` deklarovaný ve schématu serializace kontraktu dat odkazuje na třídu factory, která může deserializovat typ. Třída factory musí být součástí kolekce známých typů používané instance `DataContractSerializer`. Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>Schéma serializace DataContract

Několik schémat exportovaných pomocí `DataContractSerializer` používá typy, prvky a atributy z speciálního oboru názvů serializace kontraktu dat:

`http://schemas.microsoft.com/2003/10/Serialization`

Následuje kompletní deklarace schématu serializace kontraktu dat.

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

Měli byste si uvědomit následující:

- `ser:char` je představena tak, aby představovala znaky Unicode typu <xref:System.Char>.

- `valuespace` `xs:duration` se zmenší na seřazenou sadu, aby mohla být namapována na <xref:System.TimeSpan>.

- `FactoryType` se používá v schématech exportovaných z typů, které jsou odvozeny z <xref:System.Runtime.Serialization.ISerializable>.

## <a name="importing-non-datacontract-schemas"></a>Import schémat jiných než DataContract

`DataContractSerializer` má `ImportXmlTypes` možnost Povolit import schémat, které neodpovídají profilu XSD `DataContractSerializer` (viz vlastnost <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>). Nastavením této možnosti na `true` povolíte přijetí nevyhovujících typů schémat a jejich mapování na následující implementaci <xref:System.Xml.Serialization.IXmlSerializable> zabalení pole <xref:System.Xml.XmlNode> (liší se pouze název třídy).

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

<xref:System.DateTimeOffset> není považována za primitivní typ. Místo toho je serializován jako složitý prvek se dvěma částmi. První část představuje datum a druhá část představuje posun od data a času. Příklad serializované hodnoty DateTimeOffset je zobrazen v následujícím kódu.

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
