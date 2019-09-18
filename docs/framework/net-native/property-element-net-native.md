---
title: <Property>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54daf15c593327bf3255f40f6eb6931ffc8bd3c6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049301"
---
# <a name="property-element-net-native"></a>\<Vlastnost > element (.NET Native)
Aplikuje zásady reflexe za běhu na vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název vlastnosti.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o nebo vytváření výčtu vlastnosti, ale neumožňuje žádný dynamický přístup v době běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k vlastnosti pro povolení dynamického programování. Tato zásada zajišťuje, že vlastnost může být v době běhu nastavena nebo načtena dynamicky.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k vlastnosti, která umožňuje serializaci instancí typů pomocí knihoven, jako je například serializátor JSON Newtonsoft nebo který se má použít pro datovou vazbu.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Value|Popis|  
|-----------|-----------------|  
|*method_name*|Název vlastnosti Typ vlastnosti je definován nadřazeným [ \<typem >](type-element-net-native.md) nebo [ \<elementem > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro vlastnost Možné hodnoty jsou `Auto`, `Excluded`, `Included`a. `Required` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zásada vlastnosti není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi pro vytvoření instance `Book` objektu a zobrazení hodnot vlastností. Původní soubor default. Rd. XML pro projekt se zobrazí takto:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Soubor používá `All` hodnotu `Activate` pro zásadu pro `Book` třídu, která umožňuje přístup k konstruktorům třídy prostřednictvím reflexe. `Browse` Zásady`Book` pro třídu jsou zděděny z jejího nadřazeného oboru názvů. To je nastaveno na `Required Public`, díky čemuž jsou k dispozici metadata za běhu.  
  
 Následuje zdrojový kód pro příklad. `outputBlock` Proměnná<xref:Windows.UI.Xaml.Controls.TextBlock> představuje ovládací prvek.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Kompilace a spuštění tohoto příkladu však vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . I když jsme udělali metadata pro daný `Book` typ, nedokázali jsme využít dynamicky dostupné implementace vlastností getter. Tuto chybu můžeme opravit jedním ze dvou způsobů:  
  
- definováním `Dynamic` zásad `Book` pro typ v jeho [ \<typu >](type-element-net-native.md) element.  
  
- Přidáním vnořené [ \<vlastnosti >](property-element-net-native.md) elementu pro každou vlastnost, jejíž metoda getter by chtěla vyvolat, jako následující soubor default. Rd. XML.  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
