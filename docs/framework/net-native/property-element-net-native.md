---
title: Element &lt;Property&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676808"
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
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu vlastnost, ale neumožňuje dynamické přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Modul runtime řídí přístup k vlastnosti, které chcete povolit dynamické programování. Tato zásada zajistí, že vlastnost můžete nastavit nebo načíst dynamicky za běhu.|  
|`Serialize`|Serializace|Nepovinný atribut. Určuje runtime přístup k vlastnosti, které chcete povolit instance typu bylo serializováno modulem knihoven, jako je například serializátor Newtonsoft JSON nebo má být použit pro vytváření datových vazeb.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název vlastnosti Typ vlastnosti je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pro vlastnost. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou výslovně definované vlastnosti zásady, dědí zásady modulu runtime objektů svého nadřízeného elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá reflexi pro vytvoření instance `Book` objektů a zobrazení jeho hodnotám vlastností. Původní soubor default.rd.xml projektu se zobrazí takto:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Soubor se vztahuje `All` hodnota, která se `Activate` zásady pro `Book` třídu, která umožňuje přístup ke třídě konstruktory prostřednictvím reflexe. `Browse` Zásady `Book` třída dědí z jeho nadřazeného oboru. Je nastavené na `Required Public`, který zpřístupňuje metadat v době běhu.  
  
 Následující je zdrojový kód pro příklad. `outputBlock` Představuje proměnnou [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Ale vyvolá výjimku kompilace a spuštění tohoto příkladu [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky. I když jsme metadat `Book` typu k dispozici, jste nepovedlo se nám zpřístupnit implementace gettery vlastností dynamicky. Tuto chybu můžeme opravit buď v jedné ze dvou způsobů:  
  
-   definováním `Dynamic` zásady pro `Book` zadejte jeho [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu.  
  
-   Přidáním vnořený [ \<vlastnost >](../../../docs/framework/net-native/property-element-net-native.md) – element pro každou vlastnost, jejíž metoda getter, rádi bychom vyvolat, protože následující soubor default.rd.xml.  
  
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
