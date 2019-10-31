---
title: <MethodInstantiation> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128330"
---
# <a name="methodinstantiation-element-net-native"></a>\<element > MethodInstantiation (.NET Native)
Aplikuje zásady reflexe modulu runtime na vytvořenou obecnou metodu.  
  
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
|`Signature`|Obecné|Nepovinný atribut. Určuje pojmenované parametry metody. Více pojmenovaných parametrů je odděleno čárkami. Atribut `Signature` slouží k odlišení přetížených metod.|  
|`Arguments`|Obecné|Požadovaný atribut. Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k konstruktoru nebo metodě pro povolení dynamického programování. Tato zásada zajišťuje, že člen může být v době běhu vyvolán dynamicky.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název metody. Typ metody je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Atribut podpisu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_signature*|Určuje pojmenované parametry metody. Pokud je přítomno více parametrů, jsou odděleny čárkami.|  
  
## <a name="arguments-attribute"></a>Arguments – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_arguments*|Určuje argumenty obecného typu. Pokud je přítomno více argumentů, jsou odděleny čárkami. Každý argument musí obsahovat plně kvalifikovaný název typu.|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro metodu. Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<MethodInstantiation>` Přepisuje zásady reflexe modulu runtime příslušné otevřené obecné metody.  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
- [\<> – element metody](method-element-net-native.md)
