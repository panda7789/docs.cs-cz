---
title: Nastavení zásad direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac5d80664bbca8cf950eb2e6f37badc485c398d2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516918"
---
# <a name="runtime-directive-policy-settings"></a>Nastavení zásad direktivy modulu runtime
> [!NOTE]
>  Toto téma odkazuje na .NET Native Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Nastavení zásad direktivy běhového prostředí pro .NET Native určit dostupnost metadata pro typy a členy typu v době běhu. Bez potřeby metadat operace, které závisí na reflexi, serializace a deserializace nebo zařazování typů rozhraní .NET Framework pro COM nebo prostředí Windows Runtime nezdaří a vyvolat výjimku. Nejběžnější výjimky jsou [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a (v případě interop) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Nastavení zásad modulu runtime jsou řízeny direktivy modulu runtime (. rd.xml) soubor. Jednotlivé direktivy modulu runtime definuje zásady pro konkrétní aplikaci prvku, jako je například sestavení ( [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) prvek), typu ( [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) prvek), nebo metodu ( [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) element). Direktiva obsahuje jeden nebo více atributů, které definují typy zásad reflexe, serializace typů zásad a typy vzájemné spolupráce zásad popsané v další části. Hodnota atributu definují nastavení zásad.  
  
## <a name="policy-types"></a>Typy zásad  
 Soubory rozpoznat tři kategorie typů zásad direktivy modulu runtime: reflexe, serializace a zprostředkovatele komunikace s objekty.  
  
-   Reflexe typů zásad určují, které metadata, která je k dispozici v době běhu pro účely reflexe:  
  
    -   `Activate` Řídí přístup runtime konstruktorů, umožňuje aktivaci instancí.  
  
    -   `Browse` ovládací prvky dotazování na informace o programu elementy.  
  
    -   `Dynamic` modul runtime řídí přístup pro všechny typy a členy povolit dynamické programování.  
  
     Následující tabulka uvádí typy zásad reflexe a prvky programu, s nimiž lze je použít.  
  
    |Prvek|Aktivovat|Procházet|Dynamické|  
    |-------------|--------------|------------|-------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Serializace typů zásad určují, které metadata, která je k dispozici v době běhu k serializaci a deserializaci:  
  
    -   `Serialize` Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu bylo serializováno modulem knihovny třetích stran, jako je například serializátor Newtonsoft JSON.  
  
    -   `DataContractSerializer` Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu bylo serializováno modulem <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
    -   `DataContractJsonSerializer` Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu bylo serializováno modulem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třídy.  
  
    -   `XmlSerializer` Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu bylo serializováno modulem <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
     Následující tabulka uvádí typy zásad serializace a prvky programu, s nimiž lze je použít.  
  
    |Prvek|Serializace|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Typy vzájemné spolupráce zásad určují, které metadata, která je k dispozici v době běhu k předání odkazy na typy, typy hodnot a ukazatelů na funkce modelu COM a prostředí Windows Runtime:  
  
    -   `MarshalObject` řídí nativní zařazování do modelu COM a Windows Runtime pro typy odkazů.  
  
    -   `MarshalDelegate` řídí nativní zařazování delegujících typů jako ukazatele funkcí.  
  
    -   `MarshalStructure` řídí nativní zařazování do modelu COM a Windows Runtime pro typy hodnot.  
  
     Následující tabulka uvádí typy vzájemné spolupráce zásad a prvky programu, s nimiž lze je použít.  
  
    |Prvek|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<pole >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Vlastnost >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>Nastavení zásad  
 Každý typ zásad můžete nastavit na jednu z hodnot uvedených v následující tabulce. Všimněte si, že podporují prvky, které představují členy typů jinou sadu nastavení zásad než ostatní prvky.  
  
|Nastavení zásad|Popis|`Assembly`, `Namespace`, `Type`, a `TypeInstantiation` elementy|`Event`, `Field`, `Method`, `MethodInstantiation`, a `Property` elementy|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Povolí zásady pro všechny typy a členy, které se neodebere .NET Native řetězec nástroje.|✓||  
|`Auto`|Určuje, že má použít výchozí zásady pro typ pro tento prvek programu. To je stejný jako vynechání zásady pro tento typ zásad. `Auto` Obvykle se používá k označení, že je zásada dědí z nadřazeného elementu.|✓|✓|  
|`Excluded`|Určuje, zda je tato zásada zakázaná pro konkrétní aplikaci prvku. Například direktivy modulu runtime:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Určuje, že metadata pro `BusinessClasses.Person` třída není k dispozici buď procházet nebo dynamicky vytvořit instanci a upravte `Person` objekty.|✓|✓|  
|`Included`|Zásady umožňuje, pokud metadata pro nadřazený typ není k dispozici.||✓|  
|`Public`|Povolí zásady pro veřejné typy nebo členy, pokud řetězec nástrojů zjistí, že tento typ nebo člen není nutný a proto ji odebere. Toto nastavení se liší od `Required Public`, které zajišťuje, že metadata pro veřejné typy a členy jsou vždycky dostupné i v případě, že řetězec nástrojů shledá, že je zbytečné.|✓||  
|`PublicAndInternal`|Povolí zásady pro veřejné a vnitřní typy nebo členy, pokud řetězec nástrojů zjistí, že tento typ nebo člen není nutný a proto ji odebere. Toto nastavení se liší od `Required PublicAndInternal`, které zajišťuje, že metadata pro veřejné a vnitřní typy a členy jsou vždycky dostupné i v případě, že řetězec nástrojů shledá, že je zbytečné.|✓||  
|`Required`|Určuje, že je povolena pro člena a tato metadata bude k dispozici i v případě, že pro použití se zobrazí člen.||✓|  
|`Required Public`|Povolí zásady pro veřejné typy nebo členy a zajistí tato metadata pro veřejné typy a členy jsou vždycky dostupné. Toto nastavení se liší od `Public`, takže metadata pro veřejné typy a členy k dispozici pouze tehdy, pokud se řetězec nástrojů shledá, že je nezbytné.|✓||  
|`Required PublicAndInternal`|Povolí zásady pro veřejné a vnitřní typy nebo členy a zajistí tato metadata pro veřejné a vnitřní typy a členy jsou vždycky dostupné. Toto nastavení se liší od `PublicAndInternal`, takže metadata pro veřejné a vnitřní typy a členy k dispozici pouze tehdy, pokud se řetězec nástrojů shledá, že je nezbytné.|✓||  
|`Required All`|Vyžaduje řetězce nástrojů se všechny typy a členy Určuje, jestli máte použít a povolí zásady pro ně.|✓||  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
