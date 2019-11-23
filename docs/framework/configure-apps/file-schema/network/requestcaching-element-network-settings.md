---
title: <requestCaching> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697830"
---
# <a name="requestcaching-element-network-settings"></a>\<element > requestCaching (nastavení sítě)
Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. NET >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<requestCaching >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`isPrivateCache`|Určuje, jestli mezipaměť poskytuje izolaci mezi informacemi různých uživatelů. Výchozí hodnota je `true`. Tato hodnota by měla být `false` pro aplikace střední vrstvy.|  
|`disableAllCaching`|Určuje, že ukládání do mezipaměti je pro všechny webové odpovědi zakázané, a nedá se přepsat programově.|  
|`defaultPolicyLevel`|Jedna z hodnot ve výčtu <xref:System.Net.Cache.RequestCacheLevel>. Výchozí hodnota je `BypassCache`.|  
|`unspecifiedMaximumAge`|Určuje výchozí čas, po kterém je obsah označen jako konec platnosti.|  
  
## <a name="policylevel-attribute"></a>policyLevel – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.|  
|`BypassCache`|Vrátí prostředek ze serveru.|  
|`CacheOnly`|Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.|  
|`Revalidate`|Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí se volajícímu.|  
|`Reload`|Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.|  
|`NoCacheNoStore`|Pokud prostředek uložený v mezipaměti existuje, odstraní se. Prostředek se stáhne ze serveru a vrátí se volajícímu.|  
|`Revalidate`|Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
|[\<element > defaultFtpCachePolicy (nastavení sítě)](defaultftpcachepolicy-element-network-settings.md)|Volitelný element.<br /><br /> Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
