---
title: <Property> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128212"
---
# <a name="property-element-net-native"></a>Element > vlastnosti \<(.NET Native)
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
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název vlastnosti Typ vlastnosti je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro vlastnost Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zásada vlastnosti není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi pro vytvoření instance objektu `Book` a zobrazení hodnot vlastností. Původní soubor default. Rd. XML pro projekt se zobrazí takto:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Soubor používá `All` hodnotu na zásady `Activate` pro třídu `Book`, která umožňuje přístup ke konstruktorům třídy prostřednictvím reflexe. Zásady `Browse` pro třídu `Book` jsou zděděny z jejího nadřazeného oboru názvů. Tato nastavení je nastavená na `Required Public`, která zpřístupňuje metadata v době běhu.  
  
 Následuje zdrojový kód pro příklad. Proměnná `outputBlock` představuje ovládací prvek <xref:Windows.UI.Xaml.Controls.TextBlock>.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Kompilace a spuštění tohoto příkladu však vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . I když jsme k dispozici metadata pro `Book` typ, nedokázali jsme využít dynamicky dostupné implementace vlastností getter. Tuto chybu můžeme opravit jedním ze dvou způsobů:  
  
- definováním `Dynamic` zásad pro `Book` typu v [\<typu >](type-element-net-native.md) elementu.  
  
- Přidáním vnořené [\<vlastnosti >](property-element-net-native.md) elementu pro každou vlastnost, jejíž metoda getter by chtěla vyvolat, jako následující soubor default. Rd. XML.  
  
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
