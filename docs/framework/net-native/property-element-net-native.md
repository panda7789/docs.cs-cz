---
title: Element &lt;Property&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a857523b15631aa9c112c9c0d208d96b0ec0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396456"
---
# <a name="ltpropertygt-element-net-native"></a>Element &lt;Property&gt; (.NET Native)
Vlastnost se týká zásady reflexe modulu runtime.  
  
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
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu vlastnost ale neumožňuje žádné dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k vlastnosti, která má-li povolit dynamické programování. Tato zásada zajistí, že vlastnost můžete nastavit nebo načíst dynamicky za běhu.|  
|`Serialize`|Serializace|Nepovinný atribut. Ovládací prvky runtime přístup k vlastnosti, které chcete povolit instance typu bylo serializováno modulem knihovny například serializátor Newtonsoft JSON nebo má být použit pro datové vazby.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název vlastnosti Typ vlastnosti je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro vlastnost. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou výslovně definované zásady vlastnost dědí zásady modulu runtime objektů svého nadřízeného elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexe k vytváření instancí `Book` objektu a zobrazit jeho hodnoty vlastnosti. Původní soubor default.rd.xml pro projekt vypadá takto:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Soubor se vztahuje `All` hodnotu `Activate` zásady pro `Book` třídy, která umožňuje přístup k třída konstruktory prostřednictvím reflexe. `Browse` Zásady pro `Book` třída je zděděno od svého nadřazeného oboru názvů. To je nastaven na `Required Public`, který zpřístupní metadat za běhu.  
  
 Následuje zdrojový kód pro tento příklad. `outputBlock` Představuje proměnnou [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ale kompilování a provádění tento příklad vyvolá [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimka. I když jsme provedli metadata `Book` typu dostupný, jste se nepovedlo zpřístupnit implementace metod getter vlastnost dynamicky. Můžeme opravit tuto chybu a to buď v jedné ze dvou způsobů:  
  
-   definováním `Dynamic` zásady pro `Book` zadejte jeho [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) element.  
  
-   Přidáním vnořený [ \<vlastnost >](../../../docs/framework/net-native/property-element-net-native.md) element pro každou vlastnost getter, jejichž rádi bychom vyvolání, stejně jako následující soubor default.rd.xml.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
