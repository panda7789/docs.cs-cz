---
title: '&lt;requestCaching –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching –&gt; – Element (nastavení sítě)
Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.  
  
 \<Konfigurace >  
\<system.net>  
\<requestCaching – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`isPrivateCache`|Určuje, zda mezipaměti zajišťuje izolaci mezi informace o různých uživatelů. Výchozí hodnota je `true`. Tato hodnota by měla být `false` pro aplikace střední vrstvy.|  
|`disableAllCaching`|Určuje, že ukládání do mezipaměti je zakázán pro všechny webové odezvy a nebylo možné přepsat prostřednictvím kódu programu.|  
|`defaultPolicyLevel`|Jedna z hodnot v <xref:System.Net.Cache.RequestCacheLevel> výčtu. Výchozí hodnota je `BypassCache`.|  
|`unspecifiedMaximumAge`|Určuje výchozí dobu, po jejímž uplynutí obsah je označena jako neplatná.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel atribut, který  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí prostředků v mezipaměti, pokud je nový prostředek, délka obsahu je přesné a vypršení platnosti, úpravy a délka obsahu atributy jsou k dispozici.|  
|`BypassCache`|Vrátí prostředku ze serveru.|  
|`CacheOnly`|Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikost položky; prostředek, jinak se stáhne ze serveru a je vrácen volajícímu.|  
|`Revalidate`|Vrátí prostředků v mezipaměti, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. prostředek, jinak se stáhne ze serveru, uložené v mezipaměti a je vrácen volajícímu.|  
|`Reload`|Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí prostředek volajícímu.|  
|`NoCacheNoStore`|Pokud existuje prostředek v mezipaměti, je odstraněn. Prostředek se stáhne ze serveru a je vrácen volajícímu.|  
|`Revalidate`|Splňuje požadavek pomocí kopii prostředku v mezipaměti, pokud časové razítko je stejný jako časové razítko prostředků na serveru. jinak prostředku se stáhne ze serveru, zobrazí volajícího a je uložen v mezipaměti,|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[defaulthttpcachepolicy –](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, jestli ukládání do mezipaměti HTTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
|[\<defaultftpcachepolicy – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, jestli ukládání do mezipaměti FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
