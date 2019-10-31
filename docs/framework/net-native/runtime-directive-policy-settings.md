---
title: Nastavení zásad direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 6001e3855610e7da5262c46413b775da3bea305c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128154"
---
# <a name="runtime-directive-policy-settings"></a>Nastavení zásad direktivy modulu runtime

> [!NOTE]
> Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru. Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).

Nastavení zásad direktivy modulu runtime pro .NET Native určení dostupnosti metadat pro typy a členy typu v době běhu. Bez nezbytných metadat se operace, které spoléhají na reflexi, serializaci a deserializaci nebo zařazování typů .NET Framework do modelu COM nebo prostředí Windows Runtime mohou selhat a vyvolat výjimku. Nejběžnější výjimky jsou [MissingMetadataException](missingmetadataexception-class-net-native.md) a (v případě spolupráce) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Nastavení zásad modulu runtime se řídí souborem direktiv modulu runtime (. Rd. XML). Každá direktiva modulu runtime definuje zásadu pro konkrétní prvek programu, jako je například sestavení ( [\<](assembly-element-net-native.md) element), typ ( [\<typ >](type-element-net-native.md) prvek) nebo metoda ( [\<metoda >](method-element-net-native.md) elementu). Direktiva obsahuje jeden nebo více atributů, které definují typy zásad reflexe, typy zásad serializace a typy zásad interoperability, které jsou popsány v následující části. Hodnota atributu definuje nastavení zásad.

## <a name="policy-types"></a>Typy zásad

Soubory direktiv modulu runtime rozpoznávají tři kategorie typů zásad: reflexe, serializace a interoperabilita.

- Typy zásad reflexe určují, která metadata jsou k dispozici v době běhu pro reflexi:

  - `Activate` řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.

  - `Browse` řídí dotazování na informace o prvcích programu.

  - `Dynamic` řídí přístup za běhu ke všem typům a členům pro povolení dynamického programování.

  V následující tabulce jsou uvedeny typy zásad odrazů a prvky programu, se kterými se dají použít.

  |Prvek|Aktivací|Hlíží|dynamické|
  |-------------|--------------|------------|-------------|
  |[\<> aplikace](application-element-net-native.md)|✓|✓|✓|
  |[\<> sestavení](assembly-element-net-native.md)|✓|✓|✓|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✓|✓|✓|
  |[> události \<](event-element-net-native.md)||✓|✓|
  |[\<pole >](field-element-net-native.md)||✓|✓|
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✓|✓|✓|
  |[Metoda\<](method-element-net-native.md)||✓|✓|
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)||✓|✓|
  |[Obor názvů \<](namespace-element-net-native.md)|✓|✓|✓|
  |[Parametr \<](parameter-element-net-native.md)|✓|✓|✓|
  |[Vlastnost \<](property-element-net-native.md)||✓|✓|
  |[\<podtypy >](subtypes-element-net-native.md)|✓|✓|✓|
  |[Typ\<](type-element-net-native.md)|✓|✓|✓|
  |[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|

- Typy zásad serializace určují, která metadata jsou v době spuštění k dispozici pro serializaci a deserializaci:

  - `Serialize` řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typů serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.

  - `DataContractSerializer` řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> třídy.

  - `DataContractJsonSerializer` řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třídy.

  - `XmlSerializer` řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.

  V následující tabulce jsou uvedeny typy zásad serializace a prvky programu, se kterými se dají použít.

  |Prvek|Serializovat|DataContractSerializer|DataContractJsonSerializer|Objekt|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<> aplikace](application-element-net-native.md)|✓|✓|✓|✓|
  |[\<> sestavení](assembly-element-net-native.md)|✓|✓|✓|✓|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✓|✓|✓|✓|
  |[> události \<](event-element-net-native.md)|||||
  |[\<pole >](field-element-net-native.md)|✓||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|✓|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✓|✓|✓|✓|
  |[Metoda\<](method-element-net-native.md)|||||
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)|||||
  |[Obor názvů \<](namespace-element-net-native.md)|✓|✓|✓|✓|
  |[Parametr \<](parameter-element-net-native.md)|✓|✓|✓|✓|
  |[Vlastnost \<](property-element-net-native.md)|✓||||
  |[\<podtypy >](subtypes-element-net-native.md)|✓|✓|✓|✓|
  |[Typ\<](type-element-net-native.md)|✓|✓|✓|✓|
  |[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|✓|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|✓|

- Typy zásad spolupráce určují, která metadata jsou k dispozici v době běhu, aby předávala odkazy typy, typy hodnot a ukazatele na funkce do modelu COM a prostředí Windows Runtime:

  - `MarshalObject` řídí nativní zařazování do modelu COM a prostředí Windows Runtime pro typy odkazů.

  - `MarshalDelegate` řídí nativní zařazování typů delegátů jako ukazatelů na funkce.

  - `MarshalStructure` řídí nativní zařazování do modelu COM a prostředí Windows Runtime pro typy hodnot.

  V následující tabulce jsou uvedeny typy zásad spolupráce a prvky programu, se kterými se dají použít.

  |Prvek|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<> aplikace](application-element-net-native.md)|✓|✓|✓|
  |[\<> sestavení](assembly-element-net-native.md)|✓|✓|✓|
  |[\<AttributeImplies >](attributeimplies-element-net-native.md)|✓|✓|✓|
  |[> události \<](event-element-net-native.md)||||
  |[\<pole >](field-element-net-native.md)||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<ImpliesType >](impliestype-element-net-native.md)|✓|✓|✓|
  |[Metoda\<](method-element-net-native.md)||||
  |[\<MethodInstantiation >](methodinstantiation-element-net-native.md)||||
  |[Obor názvů \<](namespace-element-net-native.md)|✓|✓|✓|
  |[Parametr \<](parameter-element-net-native.md)|✓|✓|✓|
  |[Vlastnost \<](property-element-net-native.md)||||
  |[\<podtypy >](subtypes-element-net-native.md)|✓|✓|✓|
  |[Typ\<](type-element-net-native.md)|✓|✓|✓|
  |[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|

## <a name="policy-settings"></a>Nastavení zásad

Každý typ zásad může být nastaven na jednu z hodnot uvedených v následující tabulce. Všimněte si, že prvky, které reprezentují členy typu, podporují jinou sadu nastavení zásad než jiné prvky.

|Nastavení zásad|Popis|prvky `Assembly`, `Namespace`, `Type`a `TypeInstantiation`|prvky `Event`, `Field`, `Method`, `MethodInstantiation`a `Property`|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Povolí zásadu pro všechny typy a členy, které řetěz nástrojů .NET Native neodebírá.|✓||
|`Auto`|Určuje, že výchozí zásada by měla být použita pro typ zásad pro daný prvek programu. To je stejné jako vynechání zásad pro tento typ zásad. `Auto` se obvykle používá k označení toho, že zásady jsou zděděné z nadřazeného elementu.|✓|✓|
|`Excluded`|Určuje, že zásady jsou pro určitý prvek programu zakázané. Například Direktiva modulu runtime:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Určuje, že metadata pro třídu `BusinessClasses.Person` nejsou k dispozici, aby bylo možné procházet nebo dynamicky vytvářet instance a upravovat objekty `Person`.|✓|✓|
|`Included`|Povolí zásadu, pokud jsou k dispozici metadata pro nadřazený typ.||✓|
|`Public`|Povolí zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů neurčuje, že typ nebo člen není potřebný, a proto jej odebere. Toto nastavení se liší od `Required Public`, což zajistí, že metadata pro veřejné typy a členy jsou vždy k dispozici i v případě, že řetězec nástroje určí, že není potřebný.|✓||
|`PublicAndInternal`|Povoluje zásady pro veřejné a interní typy nebo členy, pokud řetěz nástrojů neurčuje, že typ nebo člen není zbytečný a proto jej odebere. Toto nastavení se liší od `Required PublicAndInternal`, což zajistí, že metadata pro veřejné a interní typy a členy budou vždy k dispozici i v případě, že řetězec nástroje určí, že není zapotřebí.|✓||
|`Required`|Určuje, že zásada pro člena je povolena a že metadata budou k dispozici i v případě, že se člen zdá být použit.||✓|
|`Required Public`|Povoluje zásady pro veřejné typy nebo členy a zajišťuje, že metadata pro veřejné typy a členy jsou vždy k dispozici. Toto nastavení se liší od `Public`, které zpřístupňuje metadata pro veřejné typy a členy pouze v případě, že je řetězec nástroje určen k tomu, aby byl nezbytný.|✓||
|`Required PublicAndInternal`|Povoluje zásady pro veřejné a interní typy nebo členy a zajišťuje, že metadata pro veřejné a interní typy a členy jsou vždy k dispozici. Toto nastavení se liší od `PublicAndInternal`, které zpřístupňuje metadata pro veřejné a interní typy a členy pouze v případě, že je řetězec nástroje určen k tomu, aby byl nezbytný.|✓||
|`Required All`|Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a pro ně povoluje zásady.|✓||

## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
