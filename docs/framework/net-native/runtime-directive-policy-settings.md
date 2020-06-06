---
title: Nastavení zásad direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 7a8933decaec45e8000f3f3d1717847f333deddd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "76738502"
---
# <a name="runtime-directive-policy-settings"></a>Nastavení zásad direktivy modulu runtime

> [!NOTE]
> Toto téma se týká .NET Native Developer Preview, což je předběžná verze softwaru. Verzi Preview si můžete stáhnout z [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).

Nastavení zásad direktivy modulu runtime pro .NET Native určení dostupnosti metadat pro typy a členy typu v době běhu. Bez nezbytných metadat se operace, které spoléhají na reflexi, serializaci a deserializaci nebo zařazování typů .NET Framework do modelu COM nebo prostředí Windows Runtime mohou selhat a vyvolat výjimku. Nejběžnější výjimky jsou [MissingMetadataException](missingmetadataexception-class-net-native.md) a (v případě spolupráce) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Nastavení zásad modulu runtime se řídí souborem direktiv modulu runtime (. Rd. XML). Každá direktiva modulu runtime definuje zásadu pro konkrétní prvek programu, jako je například sestavení ( [\<Assembly>](assembly-element-net-native.md) element), typ ( [\<Type>](type-element-net-native.md) prvek) nebo metoda ( [\<Method>](method-element-net-native.md) element). Direktiva obsahuje jeden nebo více atributů, které definují typy zásad reflexe, typy zásad serializace a typy zásad interoperability, které jsou popsány v následující části. Hodnota atributu definuje nastavení zásad.

## <a name="policy-types"></a>Typy zásad

Soubory direktiv modulu runtime rozpoznávají tři kategorie typů zásad: reflexe, serializace a interoperabilita.

- Typy zásad reflexe určují, která metadata jsou k dispozici v době běhu pro reflexi:

  - `Activate`řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.

  - `Browse`řídí dotazování na informace o prvcích programu.

  - `Dynamic`řídí přístup za běhu ke všem typům a členům pro povolení dynamického programování.

  V následující tabulce jsou uvedeny typy zásad odrazů a prvky programu, se kterými se dají použít.

  |Prvek|Aktivovat|Procházet|Dynamická|
  |-------------|--------------|------------|-------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||✔️|✔️|
  |[\<Field>](field-element-net-native.md)||✔️|✔️|
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||✔️|✔️|
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||✔️|✔️|
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||✔️|✔️|
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

- Typy zásad serializace určují, která metadata jsou v době spuštění k dispozici pro serializaci a deserializaci:

  - `Serialize`řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typů serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.

  - `DataContractSerializer`řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat <xref:System.Runtime.Serialization.DataContractSerializer> třídou.

  - `DataContractJsonSerializer`řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třídou.

  - `XmlSerializer`řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat <xref:System.Xml.Serialization.XmlSerializer> třídou.

  V následující tabulce jsou uvedeny typy zásad serializace a prvky programu, se kterými se dají použít.

  |Prvek|Serializovat|DataContractSerializer|DataContractJsonSerializer|Objekt|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)|||||
  |[\<Field>](field-element-net-native.md)|✔️||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)|||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)|✔️||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|✔️|

- Typy zásad spolupráce určují, která metadata jsou k dispozici v době běhu, aby předávala odkazy typy, typy hodnot a ukazatele na funkce do modelu COM a prostředí Windows Runtime:

  - `MarshalObject`řídí nativní zařazování do modelu COM a prostředí Windows Runtime pro typy odkazů.

  - `MarshalDelegate`řídí nativní zařazování typů delegátů jako ukazatelů na funkce.

  - `MarshalStructure`řídí nativní zařazování do modelu COM a prostředí Windows Runtime pro typy hodnot.

  V následující tabulce jsou uvedeny typy zásad spolupráce a prvky programu, se kterými se dají použít.

  |Prvek|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||||
  |[\<Field>](field-element-net-native.md)||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

## <a name="policy-settings"></a>Nastavení zásad

Každý typ zásad může být nastaven na jednu z hodnot uvedených v následující tabulce. Všimněte si, že prvky, které reprezentují členy typu, podporují jinou sadu nastavení zásad než jiné prvky.

|Nastavení zásad|Description|`Assembly`, `Namespace` , `Type` a `TypeInstantiation` elementy|`Event`, `Field` , `Method` , `MethodInstantiation` a `Property` elementy|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|Povolí zásadu pro všechny typy a členy, které řetěz nástrojů .NET Native neodebírá.|✔️||
|`Auto`|Určuje, že výchozí zásada by měla být použita pro typ zásad pro daný prvek programu. To je stejné jako vynechání zásad pro tento typ zásad. `Auto`se obvykle používá k označení toho, že zásady jsou zděděné z nadřazeného elementu.|✔️|✔️|
|`Excluded`|Určuje, že zásady jsou pro určitý prvek programu zakázané. Například Direktiva modulu runtime:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Určuje, že metadata pro `BusinessClasses.Person` třídu nejsou k dispozici, buď k procházení nebo k dynamickému vytváření instancí a úpravě `Person` objektů.|✔️|✔️|
|`Included`|Povolí zásadu, pokud jsou k dispozici metadata pro nadřazený typ.||✔️|
|`Public`|Povolí zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů neurčuje, že typ nebo člen není potřebný, a proto jej odebere. Toto nastavení se liší od `Required Public` , což zajišťuje, že metadata pro veřejné typy a členy jsou vždy k dispozici i v případě, že řetězec nástroje určí, že není potřebný.|✔️||
|`PublicAndInternal`|Povoluje zásady pro veřejné a interní typy nebo členy, pokud řetěz nástrojů neurčuje, že typ nebo člen není zbytečný a proto jej odebere. Toto nastavení se liší od `Required PublicAndInternal` , což zajišťuje, že metadata pro veřejné a interní typy a členy jsou vždy k dispozici i v případě, že řetězec nástroje zjistí, že není zapotřebí.|✔️||
|`Required`|Určuje, že zásada pro člena je povolena a že metadata budou k dispozici i v případě, že se člen zdá být použit.||✔️|
|`Required Public`|Povoluje zásady pro veřejné typy nebo členy a zajišťuje, že metadata pro veřejné typy a členy jsou vždy k dispozici. Toto nastavení se liší od `Public` , takže metadata pro veřejné typy a členy jsou k dispozici pouze v případě, že je řetězec nástroje určen k tomu, aby byl nezbytný.|✔️||
|`Required PublicAndInternal`|Povoluje zásady pro veřejné a interní typy nebo členy a zajišťuje, že metadata pro veřejné a interní typy a členy jsou vždy k dispozici. Toto nastavení se liší od `PublicAndInternal` , takže metadata pro veřejné a interní typy a členy jsou k dispozici pouze v případě, že je řetězec nástroje určen k tomu, aby byl nezbytný.|✔️||
|`Required All`|Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a pro ně povoluje zásady.|✔️||

## <a name="see-also"></a>Viz také

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
