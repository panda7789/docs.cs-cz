---
title: Element &lt;AttributeImplies&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92a886ab09978aef6694c37d74af49b27c37c6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a>Element &lt;AttributeImplies&gt; (.NET Native)
Definuje zásady pro elementy kódu, který je použit obsahující atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexe|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.|  
|`MarshalObject`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace s objekty|Nepovinný atribut. Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které chcete použít pro tento typ zásad. Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`. Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Reflexe zásada se vztahuje na typ a všechny její členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<AttributeImplies>` Elementu je použita, pokud jeho obsahující typ je atribut (který je třída odvozená z <xref:System.Attribute?displayProperty=nameWithType>). Pokud atribut se použije k prvku určitého programu, zásady definované `<AttributeImplies>` element platí pro daný element programu.  
  
 Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být použit.  
  
## <a name="see-also"></a>Viz také  
 [\<Typ > elementu](../../../docs/framework/net-native/type-element-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Nastavení zásad direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
