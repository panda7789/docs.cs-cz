---
title: Element &lt;MethodInstantiation&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltmethodinstantiationgt-element-net-native"></a>Element &lt;MethodInstantiation&gt; (.NET Native)
Sestavené obecné metody se týká zásady reflexe modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název metody.|  
|`Signature`|Obecné|Nepovinný atribut. Určuje pojmenované parametry metody. Více pojmenované parametry jsou oddělené čárkami. `Signature` Atribut se používá k rozlišení přetížené metody.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud jsou v něm více argumentů, jsou oddělené čárkami.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu metodu, ale neumožňuje žádné dynamické volání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktor nebo způsob povolení dynamické programování. Tato zásada zajistí, že člena nelze vyvolat dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Atribut Name.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Určuje pojmenované parametry metody. Pokud jsou v něm několik parametrů, jsou oddělené čárkami.|  
  
## <a name="arguments-attribute"></a>Argumenty atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_arguments*|Určuje argumenty obecného typu. Pokud jsou v něm více argumentů, jsou oddělené čárkami. Každý argument musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad pro metodu. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<MethodInstantiation>` Element přednost před zásadami reflexe runtime jeho odpovídající otevřete obecné metody.  
  
## <a name="see-also"></a>Viz také  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<Metoda > elementu](../../../docs/framework/net-native/method-element-net-native.md)
