---
title: <MethodInstantiation> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc8cd22c3175a2b6456f71d9dc773ce85848949
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275051"
---
# <a name="methodinstantiation-element-net-native"></a>\<MethodInstantiation > – Element (.NET Native)
Použije zásady reflexe runtime konstruovanou obecnou metodu.  
  
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
|`Signature`|Obecné|Nepovinný atribut. Určuje pojmenované parametry metody. Více pojmenované parametry jsou odděleny čárkami. `Signature` Atribut se používá k rozlišení přetížené metody.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud je více argumentů, jsou odděleny čárkami.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o nebo vytváření výčtu metody, ale nepovolí všechny dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktoru nebo metody, které chcete povolit dynamické programování. Tato zásada zajistí, že člen může být vyvolána dynamicky za běhu.|  
  
## <a name="name-attribute"></a>Název atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Určuje pojmenované parametry metody. Pokud více parametrů jsou k dispozici, jsou odděleny čárkami.|  
  
## <a name="arguments-attribute"></a>Argumenty atributu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_arguments*|Určuje argumenty obecného typu. Pokud je více argumentů, jsou odděleny čárkami. Každý argument musí obsahovat plně kvalifikovaného názvu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Toto nastavení platí pro tento typ zásad pro metodu. Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Použije zásady reflexe pro typ a všechny její členy.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<MethodInstantiation>` Prvek přepisuje zásady reflexe modulu runtime jeho odpovídající otevřít obecné metody.  
  
## <a name="see-also"></a>Viz také:
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [\<Metoda > – Element](../../../docs/framework/net-native/method-element-net-native.md)
