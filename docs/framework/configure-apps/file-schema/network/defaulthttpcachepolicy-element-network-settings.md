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
ms.openlocfilehash: 20d9b92ca2bbffd6b98b8641e5cef5e567cb84cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177373"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<defaulthttpcachepolicy – > – Element (nastavení sítě)
Popisuje, zda HTTP, ukládání do mezipaměti je aktivní a popisuje výchozí zásady ukládání do mezipaměti.  
  
 \<Konfigurace >  
\<system.net>  
\<requestCaching>  
\<defaultHttpCachePolicy>  
  
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
|`maximumAge`|Určuje maximální dobu, než objekt uložený v mezipaměti je označena jako neplatná.|  
|`maximumStale`|Určuje maximální dobu, po čase vypočítané aktuálnosti před objekt uložený v mezipaměti je označena jako neplatná.|  
|`minimumFresh`|Určuje minimální dobu pro objekt uložený v mezipaměti k považovat za čerstvý.|  
|`policyLevel`|Určuje, zda je automatické zásady ukládání do mezipaměti, nebo zda obejít mezipaměť. Výchozí hodnota je `BypassCache`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `policyLevel` atribut je buď `BypassCache` nebo `Default`.  
  
 Hodnoty `maximumAge`, `maximumStale`, a `minimumFresh` prvky jsou buď explicitní čas intervalu ve formátu *d*. *hh*:*mm*:*ss* (dny, hodiny, minuty a sekundy), nebo konstanty `minValue` nebo `maxValue`podle potřeby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat minimální aktuální čas šest hodin, maximální stáří času o dva dny a maximální zastaralé dobu čtyř hodin.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
