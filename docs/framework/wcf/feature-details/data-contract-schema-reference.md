---
title: Schéma kontraktů dat – referenční informace
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593565"
---
# <a name="data-contract-schema-reference"></a>Schéma kontraktů dat – referenční informace

Toto téma popisuje podmnožinu schématu XML (XSD) používaného <xref:System.Runtime.Serialization.DataContractSerializer> pro popis typů modulu CLR (Common Language Runtime) pro serializaci XML.

## <a name="datacontractserializer-mappings"></a>Mapování DataContractSerializer

`DataContractSerializer`Mapuje typy CLR na XSD při exportu metadat ze služby Windows Communication Foundation (WCF) pomocí koncového bodu metadat nebo nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [serializátor kontraktu dat](data-contract-serializer.md).

`DataContractSerializer`Také MAPUJE XSD na typy CLR, pokud se Svcutil. exe používá pro přístup k dokumentům WSDL (Web Services Description Language) nebo XSD a k vygenerování kontraktů dat pro služby nebo klienty.

Pouze instance schématu XML, které odpovídají požadavkům uvedeným v tomto dokumentu, lze namapovat na typy CLR pomocí `DataContractSerializer` .

### <a name="support-levels"></a>Úrovně podpory

`DataContractSerializer`Poskytuje následující úrovně podpory pro danou funkci schématu XML:

- **Podporuje**se. Existuje explicitní mapování z této funkce na typy CLR nebo atributy (nebo obojí) pomocí `DataContractSerializer` .

- **Ignoruje**se. Tato funkce je povolena v schématech importovaných `DataContractSerializer` , ale nemá žádný vliv na generování kódu.

- **Zakázané**. Nástroj nepodporuje `DataContractSerializer` Import schématu pomocí funkce. Například Svcutil. exe při přístupu k WSDL se schématem, které tuto funkci používá, se vrátí k použití <xref:System.Xml.Serialization.XmlSerializer> namísto. Toto je ve výchozím nastavení.

## <a name="general-information"></a>Obecné informace

- Obor názvů schématu je popsán ve [schématu XML](https://www.w3.org/2001/XMLSchema). V tomto dokumentu je použita předpona "XS".

- Všechny atributy s oborem názvů bez schématu jsou ignorovány.

- Jakékoli poznámky (kromě těch, které jsou popsány v tomto dokumentu) se ignorují.

### <a name="xsschema-attributes"></a>\<xs:schema>: atributy

|Atribut|Kontraktu DataContract|
|---------------|------------------|
|`attributeFormDefault`|Přeskočen.|
|`blockDefault`|Přeskočen.|
|`elementFormDefault`|Musí být kvalifikován. Všechny elementy musí být kvalifikovány, aby bylo schéma podporováno nástrojem `DataContractSerializer` . To lze provést buď nastavením xs:schema/@elementFormDefault na "kvalifikovaný", nebo nastavením xs:element/@form na "kvalifikovaný" pro každou deklaraci jednotlivého prvku.|
|`finalDefault`|Přeskočen.|
|`Id`|Přeskočen.|
|`targetNamespace`|Podporováno a mapováno na obor názvů kontraktu dat. Pokud tento atribut není zadán, je použit prázdný obor názvů. Nemůže se jednat o vyhrazený obor názvů `http://schemas.microsoft.com/2003/10/Serialization/` .|
|`version`|Přeskočen.|

### <a name="xsschema-contents"></a>\<xs:schema>: obsah

|Obsah|Schéma|
|--------------|------------|
|`include`|Podporuje se. `DataContractSerializer`podporuje xs: include a xs: import. Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazy na to, kdy jsou metadata načtena z místního souboru. Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. `include` dokumenty schématu d se ignorují.|
|`redefine`|Zakázán. Z `xs:redefine` bezpečnostních důvodů je použití zakázáno z `DataContractSerializer` důvodu zabezpečení: `x:redefine` vyžaduje, `schemaLocation` aby následovala. Za určitých okolností Svcutil. exe využívající DataContract omezí použití `schemaLocation` .|
|`import`|Podporuje se. `DataContractSerializer`podporuje `xs:include` a `xs:import` . Svcutil. exe však omezuje následující `xs:include/@schemaLocation` a `xs:import/@location` odkazy na to, kdy jsou metadata načtena z místního souboru. Seznam souborů schématu musí být předán pomocí mechanismu mimo pásmo, a ne prostřednictvím `include` v tomto případě. `include` dokumenty schématu d se ignorují.|
|`simpleType`|Podporuje se. Přečtěte si část `xs:simpleType`.|
|`complexType`|Podporováno, mapuje se na kontrakty dat. Přečtěte si část `xs:complexType`.|
|`group`|Přeskočen. `DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` . Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.|
|`attributeGroup`|Přeskočen. `DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` . Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.|
|`element`|Podporuje se. Viz deklarace globálních elementů (připravený).|
|`attribute`|Přeskočen. `DataContractSerializer`nepodporuje použití `xs:group` , `xs:attributeGroup` , a `xs:attribute` . Tato deklarace jsou ignorována jako podřízené položky `xs:schema` , ale nelze na ni odkazovat v rámci `complexType` nebo jiných podporovaných konstrukcích.|
|`notation`|Přeskočen.|

## <a name="complex-types--xscomplextype"></a>Komplexní typy –\<xs:complexType>

### <a name="general-information"></a>Obecné informace

Každý komplexní typ \<xs:complexType> se mapuje na kontrakt dat.

### <a name="xscomplextype-attributes"></a>\<xs:complexType>: atributy

|Atribut|Schéma|
|---------------|------------|
|`abstract`|Hodnota musí být false (výchozí).|
|`block`|Zakázán.|
|`final`|Přeskočen.|
|`id`|Přeskočen.|
|`mixed`|Hodnota musí být false (výchozí).|
|`name`|Podporováno a mapováno na název kontraktu dat. Pokud v názvu existují tečky, je proveden pokus o mapování typu na vnitřní typ. Například komplexní typ nazvaný `A.B` mapuje typ kontraktu dat, který je vnitřní typ typu s názvem kontraktu dat `A` , ale pouze v případě, že takový typ kontraktu dat existuje. Je možné použít více než jednu úroveň vnoření: `A.B.C` může to být například vnitřní typ, ale pouze pokud `A` `A.B` existuje.|

### <a name="xscomplextype-contents"></a>\<xs:complexType>: obsah

|Obsah|Schéma|
|--------------|------------|
|`simpleContent`|Rozšíření jsou zakázána.<br /><br /> Omezení je povoleno pouze z `anySimpleType` .|
|`complexContent`|Podporuje se. Viz "dědičnost".|
|`group`|Zakázán.|
|`all`|Zakázán.|
|`choice`|Forbidden|
|`sequence`|Podporováno, mapuje se na datové členy kontraktu dat.|
|`attribute`|Zakázáno, i když use = "zakázáno" (s jednou výjimkou). Jsou podporovány pouze volitelné atributy z oboru názvů schématu standardní serializace. Nemapují se na datové členy v programovacím modelu kontraktu dat. V současné době pouze jeden takový atribut má význam a je popsán v oddílu ISerializable. Všechny ostatní jsou ignorovány.|
|`attributeGroup`|Zakázán. Ve verzi WCF v1 `DataContractSerializer` ignoruje přítomnost `attributeGroup` uvnitř `xs:complexType` .|
|`anyAttribute`|Zakázán.|
|obsahovat|Mapuje se na kontrakt dat bez datových členů.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:sequence>ve komplexním typu: atributy

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`maxOccurs`|Musí mít hodnotu 1 (výchozí).|
|`minOccurs`|Musí mít hodnotu 1 (výchozí).|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:sequence>v komplexním typu: obsah

|Obsah|Schéma|
|--------------|------------|
|`element`|Každá instance se mapuje na datový člen.|
|`group`|Zakázán.|
|`choice`|Zakázán.|
|`sequence`|Zakázán.|
|`any`|Zakázán.|
|obsahovat|Mapuje se na kontrakt dat bez datových členů.|

## <a name="elements--xselement"></a>Elementu\<xs:element>

### <a name="general-information"></a>Obecné informace

`<xs:element>`může dojít v následujících kontextech:

- Může k tomu dojít v rámci `<xs:sequence>` , který popisuje datový člen pravidelného kontraktu dat (bez kolekce). V takovém případě `maxOccurs` musí být atribut 1. (Hodnota 0 není povolená).

- Může k tomu dojít v rámci `<xs:sequence>` , který popisuje datový člen kontraktu dat kolekce. V tomto případě `maxOccurs` musí být atribut větší než 1 nebo "Unbounded".

- Může se vyskytnout v rámci `<xs:schema>` deklarace jako globální element (připravený).

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:element>s hodnota atributu maxOccurs = 1 v rámci \<xs:sequence> (datové členy)

|Atribut|Schéma|
|---------------|------------|
|`ref`|Zakázán.|
|`name`|Podporováno, mapuje se na název datového členu.|
|`type`|Podporováno, je mapováno na typ datového člena. Další informace naleznete v tématu mapování typů a primitivních hodnot. Pokud není zadán (a element neobsahuje anonymní typ), `xs:anyType` předpokládá se.|
|`block`|Přeskočen.|
|`default`|Zakázán.|
|`fixed`|Zakázán.|
|`form`|Musí být kvalifikován. Tento atribut lze nastavit pomocí `elementFormDefault` `xs:schema` .|
|`id`|Přeskočen.|
|`maxOccurs`|1|
|`minOccurs`|Mapuje se na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost datového členu ( `IsRequired` true, pokud `minOccurs` je hodnota 1).|
|`nillable`|Má vliv na mapování typů. Viz mapování typů a primitivních hodnot.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:element>s maxOccurs>1 v rámci \<xs:sequence> (kolekcí)

- Provede mapování na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .

- V typech kolekcí je povolena pouze jedna xs: element v rámci typu xs: Sequence.

 Kolekce mohou mít následující typy:

- Běžné kolekce (například pole).

- Kolekce slovníku (mapování jedné hodnoty na jinou, například a <xref:System.Collections.Hashtable> ).

- Jediný rozdíl mezi slovníkem a polem typu dvojice klíč/hodnota je ve vygenerovaném programovacím modelu. Existuje mechanismus pro anotaci schématu, který lze použít k označení toho, že daný typ je kolekce slovníku.

Pravidla pro `ref` `block` atributy,,, `default` `fixed` , `form` a `id` jsou stejná jako pro případ bez kolekce. Další atributy jsou obsaženy v následující tabulce.

|Atribut|Schéma|
|---------------|------------|
|`name`|Podporováno, mapuje na <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost v `CollectionDataContractAttribute` atributu.|
|`type`|Podporováno, mapuje na typ uložený v kolekci.|
|`maxOccurs`|Je větší než 1 nebo "Unbounded". Schéma DC by mělo používat "Unbounded".|
|`minOccurs`|Přeskočen.|
|`nillable`|Má vliv na mapování typů. Tento atribut se pro kolekce slovníku ignoruje.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:element>v rámci \<xs:schema> deklarace globálních elementů

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
|`name`|Podporuje se. Viz definice přidružených GEDs.|
|`nillable`|Pro přidruženou GEDs musí mít hodnotu true.|
|`substitutionGroup`|Zakázáno v přidružených GEDs.|
|`type`|Podporováno a musí odpovídat přidruženému typu pro přidružené GEDs (Pokud element neobsahuje anonymní typ).|

### <a name="xselement-contents"></a>\<xs:element>: obsah

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Podporováno. *|
|`complexType`|Podporováno. *|
|`unique`|Přeskočen.|
|`key`|Přeskočen.|
|`keyref`|Přeskočen.|
|trhnout|Podporuje se.|

\*Při použití `simpleType` a `complexType,` mapování anonymních typů je stejný jako u neanonymních typů s tím rozdílem, že neexistují žádné anonymní kontrakty dat, a proto je vytvořen pojmenovaný kontrakt dat s vygenerovaným názvem odvozeným z názvu elementu. Pravidla pro anonymní typy jsou v následujícím seznamu:

- Podrobnosti implementace WCF: Pokud `xs:element` název neobsahuje tečky, anonymní typ se mapuje na vnitřní typ typu kontraktu s vnějšími daty. Pokud název obsahuje tečky, je výsledný typ kontraktu dat nezávislý (nejedná se o vnitřní typ).

- Název kontraktu generovaných dat vnitřního typu je název kontraktu dat vnějšího typu následovaný tečkou, názvem elementu a řetězcem "typ".

- Pokud již existuje kontrakt dat s tímto názvem, je název jedinečný připojením "1", "2", "3" a tak dále, dokud nebude vytvořen jedinečný název.

## <a name="simple-types---xssimpletype"></a>Jednoduché typy –\<xs:simpleType>

### <a name="xssimpletype-attributes"></a>\<xs:simpleType>: atributy

|Atribut|Schéma|
|---------------|------------|
|`final`|Přeskočen.|
|`id`|Přeskočen.|
|`name`|Podporováno, mapuje se na název kontraktu dat.|

### <a name="xssimpletype-contents"></a>\<xs:simpleType>: obsah

|Obsah|Schéma|
|--------------|------------|
|`restriction`|Podporuje se. Mapuje se na kontrakty dat výčtu. Tento atribut je ignorován, pokud neodpovídá vzoru výčtu. Podívejte se na `xs:simpleType` část omezení.|
|`list`|Podporuje se. Provede mapování na označení kontraktů dat výčtu. Viz `xs:simpleType` část seznamy.|
|`union`|Zakázán.|

### \<xs:restriction>

- Omezení komplexního typu jsou podporována pouze pro základní = `xs:anyType` .

- Jednoduchá omezení typu `xs:string` , která nemají žádné charakteristiky omezení jiné než `xs:enumeration` jsou namapovány na kontrakty dat výčtu.

- Všechna ostatní omezení jednoduchých typů jsou namapována na typy, které omezují. Například omezení `xs:int` mapování na celé číslo, stejně jako na `xs:int` sebe samé. Další informace o mapování primitivního typu najdete v tématu mapování typů a primitivních typů.

### <a name="xsrestriction-attributes"></a>\<xs:restriction>: atributy

|Atribut|Schéma|
|---------------|------------|
|`base`|Musí se jednat o podporovaný jednoduchý typ nebo `xs:anyType` .|
|`id`|Přeskočen.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction>pro všechny ostatní případy: obsah

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
|trhnout|Podporuje se.|

## <a name="enumeration"></a>Výčet

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction>pro výčty: atributy

|Atribut|Schéma|
|---------------|------------|
|`base`|Pokud je přítomen, musí být `xs:string` .|
|`id`|Přeskočen.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction>pro výčty: obsah

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
|`enumeration`|Podporuje se. Výčet "ID" se ignoruje a hodnota "value" se mapuje na název hodnoty ve kontraktu dat výčtu.|
|`whiteSpace`|Zakázán.|
|`pattern`|Zakázán.|
|obsahovat|Podporováno, mapuje se na prázdný typ výčtu.|

 Následující kód ukazuje třídu výčtu jazyka C#.

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

Tato třída je mapována na následující schéma pomocí `DataContractSerializer` . Pokud hodnoty výčtu začínají na 1, `xs:annotation` bloky se nevygenerují.

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

### \<xs:list>

`DataContractSerializer`mapuje výčtové typy označené `System.FlagsAttribute` s `xs:list` odvozeným z `xs:string` . Žádné jiné `xs:list` varianty nejsou podporovány.

### <a name="xslist-attributes"></a>\<xs:list>: atributy

|Atribut|Schéma|
|---------------|------------|
|`itemType`|Zakázán.|
|`id`|Přeskočen.|

### <a name="xslist-contents"></a>\<xs:list>: obsah

|Obsah|Schéma|
|--------------|------------|
|`simpleType`|Musí být omezením `xs:string` použití `xs:enumeration` omezující vlastnosti.|

Pokud hodnota výčtu nedodržuje mocninu 2 (výchozí pro příznaky), hodnota je uložena v `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.

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

Kontrakt dat může dědit od jiného kontraktu dat. Tyto kontrakty dat jsou mapovány na základ a jsou odvozeny pomocí typů rozšíření pomocí `<xs:extension>` konstrukce schématu XML.

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

### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent>: atributy

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`mixed`|Hodnota musí být false.|

### <a name="xscomplexcontent-contents"></a>\<xs:complexContent>: obsah

|Obsah|Schéma|
|--------------|------------|
|`restriction`|Zakázáno, s výjimkou případů, kdy je Base = " `xs:anyType` ". Druhý je ekvivalentní umístění obsahu `xs:restriction` přímo pod kontejnerem `xs:complexContent` .|
|`extension`|Podporuje se. Provede mapování na dědičnost kontraktu dat.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension>v \<xs:complexContent> : atributy

|Atribut|Schéma|
|---------------|------------|
|`id`|Přeskočen.|
|`base`|Podporuje se. Provede mapování základního typu kontraktu dat, z něhož tento typ dědí.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:extension>v \<xs:complexContent> : obsah

Pravidla jsou stejná jako u `<xs:complexType>` obsahu.

Pokud `<xs:sequence>` je k dispozici, jeho členské prvky budou mapovány na další datové členy, které jsou přítomny v odvozeném kontraktu dat.

Pokud odvozený typ obsahuje element se stejným názvem jako element v základním typu, je deklarace duplicitních prvků mapována na datový člen s názvem, který je vygenerován jako jedinečný. Kladné celočíselná čísla jsou přidána do názvu datového členu ("Člen1", "member2" atd.), dokud nebude nalezen jedinečný název. Naopak

- Pokud má odvozená kontrakt dat datový člen se stejným názvem a typem jako datový člen v základní kontraktu dat, `DataContractSerializer` vygeneruje tento odpovídající prvek v odvozeném typu.

- Pokud má odvozená kontrakt dat datový člen se stejným názvem jako datový člen v základní kontraktu dat, ale jiný typ, `DataContractSerializer` importuje schéma s prvkem typu `xs:anyType` v obou základních typech i v deklaracích odvozených typů. Původní název typu se zachová v `xs:annotations/xs:appInfo/ser:ActualType/@Name` .

Obě varianty mohou vést ke schématu s nejednoznačným obsahem modelu, který závisí na pořadí příslušných datových členů.

## <a name="typeprimitive-mapping"></a>Mapování typů a primitivních hodnot

`DataContractSerializer`Používá následující mapování pro primitivní typy schémat XML.

|Typ XSD|Typ .NET|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|<xref:System.DateTime>a <xref:System.TimeSpan> pro posun. Viz serializace DateTimeOffset níže.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<xref:System.Byte>skupin.|
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

V .NET Framework verze 1,0 <xref:System.Runtime.Serialization.ISerializable> byla představena jako obecný mechanismus pro serializaci objektů pro trvalost nebo přenos dat. Existuje mnoho typů .NET Framework, které implementují `ISerializable` a které je možné předat mezi aplikacemi. <xref:System.Runtime.Serialization.DataContractSerializer>přirozeně poskytuje podporu pro `ISerializable` třídy. `DataContractSerializer`Mapy `ISerializable` implementují typy schématu, které se liší pouze názvem QName (kvalifikovaný název) typu a jsou účinné kolekce vlastností. Například `DataContractSerializer` mapuje <xref:System.Exception> na následující typ XSD v `http://schemas.datacontract.org/2004/07/System` oboru názvů.

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

Volitelný atribut `ser:FactoryType` deklarovaný ve schématu serializace kontraktu dat odkazuje na třídu factory, která může deserializovat typ. Třída factory musí být součástí kolekce známých typů `DataContractSerializer` používané instance. Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>Schéma serializace DataContract

Několik schémat vyexportovaných `DataContractSerializer` typy použití, prvky a atributy z speciálního oboru názvů serializace kontraktu dat:

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

- `ser:char`je představena pro reprezentaci znaků Unicode typu <xref:System.Char> .

- `valuespace`Z `xs:duration` je snížen na seřazenou sadu, aby mohla být namapována na <xref:System.TimeSpan> .

- `FactoryType`se používá v schématech exportovaných z typů, které jsou odvozeny z <xref:System.Runtime.Serialization.ISerializable> .

## <a name="importing-non-datacontract-schemas"></a>Import schémat jiných než DataContract

`DataContractSerializer`má `ImportXmlTypes` možnost Povolit import schémat, která neodpovídají `DataContractSerializer` profilu XSD (viz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost). Nastavením této možnosti `true` umožníte přijetí nevyhovujících typů schémat a jejich mapování na následující implementaci a <xref:System.Xml.Serialization.IXmlSerializable> zabalení pole <xref:System.Xml.XmlNode> (pouze název třídy se liší).

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

Není <xref:System.DateTimeOffset> považována za primitivní typ. Místo toho je serializován jako složitý prvek se dvěma částmi. První část představuje datum a druhá část představuje posun od data a času. Příklad serializované hodnoty DateTimeOffset je zobrazen v následujícím kódu.

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

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [Použití kontraktů dat](using-data-contracts.md)
