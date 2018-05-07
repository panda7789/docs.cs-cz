---
title: Nastavení zásad direktivy modulu runtime
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51a0538670a834435aff8d2b6c81b78450fe47f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="runtime-directive-policy-settings"></a>Nastavení zásad direktivy modulu runtime
> [!NOTE]
>  Toto téma se týká .NET nativní Developer Preview, což je předběžná verze softwaru. Preview z si můžete stáhnout [webu Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (vyžaduje registraci).  
  
 Nastavení zásad direktivy modulu runtime pro .NET Native určit dostupnost metadata pro typy a členy typu za běhu. Bez potřeby metadata můžete operace, které závisí na reflexi, serializace a deserializace nebo zařazování typů rozhraní .NET Framework do modelu COM nebo prostředí Windows Runtime selže a vyvolá výjimku. Nejběžnější výjimky jsou [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a (v případě zprostředkovatel komunikace s objekty) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Nastavení zásad runtime jsou řízeny direktivy modulu runtime (. rd.xml) souboru. Každý direktivy modulu runtime definuje zásady pro element určitého programu, například sestavení ( [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md) element), typ ( [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element), nebo metodu ( [ \<metoda >](../../../docs/framework/net-native/method-element-net-native.md) element). Direktiva obsahuje jeden nebo více atributů, které definují typy zásad reflexe, typy zásad serializace a typy spolupráce zásad popsané v další části. Hodnota atributu definuje nastavení zásad.  
  
## <a name="policy-types"></a>Typy zásad  
 Direktivy modulu runtime soubory rozpoznat tří kategorií typy zásad: reflexe serializace a zprostředkovatel komunikace s objekty.  
  
-   Typy zásad reflexe určit, které metadata, která je k dispozici v době běhu pro reflexi:  
  
    -   `Activate` Ovládací prvky runtime přístup k konstruktory, chcete-li povolit aktivace instancí.  
  
    -   `Browse` ovládací prvky dotazování na informace o programu elementy.  
  
    -   `Dynamic` ovládací prvky runtime přístupu pro všechny typy a členy pro povolení dynamické programování.  
  
     Následující tabulka uvádí typy zásad reflexe a prvky programu, pomocí kterých lze použít.  
  
    |Prvek|Aktivovat|Procházet|dynamické|  
    |-------------|--------------|------------|-------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
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
  
-   Typy zásad serializace určit, které metadata, která je k dispozici v době běhu k serializaci a deserializaci:  
  
    -   `Serialize` ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu do knihovny třetích stran, jako je například serializátor Newtonsoft JSON serializovat.  
  
    -   `DataContractSerializer` Řídí přístup runtime konstruktory, pole a vlastnosti, aby instance typu bylo serializováno modulem <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
    -   `DataContractJsonSerializer` Řídí přístup runtime konstruktory, pole a vlastnosti, aby instance typu bylo serializováno modulem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třídy.  
  
    -   `XmlSerializer` Řídí přístup runtime konstruktory, pole a vlastnosti, aby instance typu bylo serializováno modulem <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
     Následující tabulka uvádí typy zásad serializace a prvky programu, pomocí kterých lze použít.  
  
    |Prvek|serializace|DataContractSerializer|DataContractJsonSerializer|Třídy XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
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
  
-   Typy spolupráce zásad určují, které metadata, která je k dispozici v době běhu předat odkazy typy, typy hodnot a ukazatelů na funkce COM a prostředí Windows Runtime:  
  
    -   `MarshalObject` ovládací prvky nativní zařazování COM a prostředí Windows Runtime pro odkazové typy.  
  
    -   `MarshalDelegate` ovládací prvky nativní zařazování delegáta typů jako ukazatelů na funkce.  
  
    -   `MarshalStructure` ovládací prvky nativní zařazování COM a prostředí Windows Runtime pro typy hodnot.  
  
     Následující tabulka uvádí typy spolupráce zásad a prvky programu, pomocí kterých lze použít.  
  
    |Prvek|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Událost >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)||||  
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
 Každý typ zásad můžete nastavit na jedno z hodnoty uvedené v následující tabulce. Poznámka: aby prvky, které představují členy typu podporují jinou sadu nastavení zásad než další prvky.  
  
|Nastavení zásad|Popis|`Assembly`, `Namespace`, `Type`, a `TypeInstantiation` elementy|`Event`, `Field`, `Method`, `MethodInstantiation`, a `Property` elementy|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Umožňuje zásady pro všechny typy a členy, kteří řetězu .NET Native nástroj neodstraní.|✓||  
|`Auto`|Určuje, že by měl používat výchozí zásady pro typ zásad pro daný element programu. Toto je stejný jako vynechání zásady pro tento typ zásad. `Auto` Obvykle se používá k označení, že zásady je zděděn z nadřazeného elementu.|✓|✓|  
|`Excluded`|Určuje, že zásada je zakázána pro element určitého programu. Například direktivy modulu runtime:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Určuje, že metadata pro `BusinessClasses.Person` třída není k dispozici buď procházet nebo dynamicky vytvořit a upravit `Person` objekty.|✓|✓|  
|`Included`|Umožňuje zásadu metadata pro nadřazený typ je k dispozici.||✓|  
|`Public`|Umožňuje zásady pro veřejné typy nebo členy, pokud řetězu nástroj zjistí, že typ nebo člen je zbytečné a proto ji odstraní. Toto nastavení se liší od `Required Public`, což zajistí, aby metadata pro veřejné typy a členy je vždy k dispozici i v případě řetězu nástroj určuje, že není nutné.|✓||  
|`PublicAndInternal`|Umožňuje zásady pro veřejné a interní typy nebo členy, pokud řetězu nástroj zjistí, že typ nebo člen je zbytečné a proto ji odstraní. Toto nastavení se liší od `Required PublicAndInternal`, což zajistí, aby metadata pro veřejné a interní typy a členy je vždy k dispozici i v případě řetězu nástroj určuje, že není nutné.|✓||  
|`Required`|Určuje, že je povolena pro člena a aby metadata bude k dispozici, i když se zobrazí člen má být použit.||✓|  
|`Required Public`|Umožňuje zásady pro veřejné typy nebo členy a zajišťuje, aby metadata pro veřejných typů a členů je vždy k dispozici. Toto nastavení se liší od `Public`, takže metadata pro veřejné typy a členy k dispozici pouze v případě, že řetězu nástroj určuje, zda je nutné.|✓||  
|`Required PublicAndInternal`|Umožňuje zásady pro veřejné a interní typy nebo členy a zajišťuje, aby metadata pro veřejné a interní typů a členů je vždy k dispozici. Toto nastavení se liší od `PublicAndInternal`, takže metadata pro veřejné a interní typy a členy k dispozici pouze v případě, že řetězu nástroj určuje, zda je nutné.|✓||  
|`Required All`|Vyžaduje řetězu nástroj chránit všechny typy a členy, jestli používají a umožňuje zásady pro ně.|✓||  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
