---
title: <defaultFtpCachePolicy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: fd1649edbf7a2c8546992019df667f27df68e02c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698321"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>@no__t – element > 0defaultFtpCachePolicy (nastavení sítě)
Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultFtpCachePolicy >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`policyLevel`|Určuje zásady ukládání do mezipaměti FTP. Výchozí hodnota je `Default`.|  
  
## <a name="policylevel-attribute"></a>policyLevel – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.|  
|`BypassCache`|Vrátí prostředek ze serveru.|  
|`CacheOnly`|Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.|  
|`Revalidate`|Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí volajícímu.|  
|`Reload`|Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.|  
|`NoCacheNoStore`|Pokud prostředek uložený v mezipaměti existuje, odstraní se. Prostředek se stáhne ze serveru a vrátí se volajícímu.|  
|`Revalidate`|Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit zásady ukládání do mezipaměti FTP `NoCacheNoStore`.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma nastavení sítě](index.md)
