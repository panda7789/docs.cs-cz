---
title: <defaultHttpCachePolicy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088421"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<element > defaultHttpCachePolicy (nastavení sítě)
Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultHttpCachePolicy >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maximumAge`|Určuje maximální časový interval, po jehož uplynutí je objekt uložený v mezipaměti označený jako neplatný.|  
|`maximumStale`|Určuje maximální dobu, po jejímž uplynutí je vypočítaná doba aktuálnosti, než je objekt uložený v mezipaměti označený jako neplatný.|  
|`minimumFresh`|Určuje minimální dobu, po kterou bude objekt v mezipaměti považován za čerstvý.|  
|`policyLevel`|Určuje, jestli jsou zásady ukládání do mezipaměti automatické, nebo jestli se mezipaměť nepoužívá. Výchozí hodnota je `BypassCache`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota atributu `policyLevel` je buď `BypassCache` nebo `Default`.  
  
 Hodnoty pro prvky `maximumAge`, `maximumStale`a `minimumFresh` jsou buď explicitním časovým intervalem formátu *d*. *HH*:*mm*:*SS* (dny, hodiny, minuty a sekundy) nebo konstanty `minValue` nebo `maxValue`podle potřeby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat minimální dobu v čase 6 hodin, maximální dobu stáří dvou dnů a maximální zastaralou dobu čtyř hodin.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma nastavení sítě](index.md)
