---
title: "&lt;defaultftpcachepolicy –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultftpcachepolicy –&gt; – Element (nastavení sítě)
Popisuje, jestli ukládání do mezipaměti FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.  
  
 \<Konfigurace >  
\<System.NET >  
\<requestCaching – >  
\<defaultftpcachepolicy – >  
  
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
|`policyLevel`|Určuje FTP zásady ukládání do mezipaměti. Výchozí hodnota je `Default`.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel atribut, který  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`Default`|Vrátí prostředků v mezipaměti, pokud je nový prostředek, délka obsahu je přesné a vypršení platnosti, úpravy a délka obsahu atributy jsou k dispozici.|  
|`BypassCache`|Vrátí prostředku ze serveru.|  
|`CacheOnly`|Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikosti položky.|  
|`CacheIfAvailable`|Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikost položky; prostředek, jinak se stáhne ze serveru a je vrácen volajícímu.|  
|`Revalidate`|Vrátí prostředků v mezipaměti, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. jinak prostředek stažený ze serveru, uložené v mezipaměti a vrácen volajícímu.|  
|`Reload`|Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí prostředek volajícímu.|  
|`NoCacheNoStore`|Pokud existuje prostředek v mezipaměti, je odstraněn. Prostředek se stáhne ze serveru a je vrácen volajícímu.|  
|`Revalidate`|Splňuje požadavek pomocí kopii prostředku v mezipaměti, pokud časové razítko je stejný jako časové razítko prostředků na serveru. jinak prostředek stažený ze serveru, uvedené volajícímu a uložené v mezipaměti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching –](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit k serveru FTP ukládání do mezipaměti zásady `NoCacheNoStore`.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
