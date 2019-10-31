---
title: <Event> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 6966caede63faafa718b760be879f6bc6cbd3ab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128495"
---
# <a name="event-element-net-native"></a>\<element > události (.NET Native)
Aplikuje zásadu reflexe modulu runtime na událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Name`|Obecné|Požadovaný atribut. Určuje název události.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování na informace o nebo vytváření výčtu události, ale nepovoluje žádný dynamický přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu k události pro povolení dynamického programování. Tato zásada zajišťuje, že událost může být v době běhu zpracována dynamicky.|  
  
## <a name="name-attribute"></a>Atribut Name  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*method_name*|Název události Typ události je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Všechny ostatní atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít pro tento typ zásad pro událost Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`. Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zásada události není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
