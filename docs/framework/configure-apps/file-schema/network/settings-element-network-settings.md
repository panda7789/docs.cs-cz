---
title: '&lt;nastavení&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3f717705a6cd4cc29fe333f5012c7fec466d350b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752475"
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;nastavení&gt; – Element (nastavení sítě)
Nakonfiguruje možnosti základní sítě <xref:System.Net?displayProperty=nameWithType> oboru názvů.  
  
 \<Konfigurace >  
\<system.net>  
\<Nastavení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[HttpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.|  
|[HttpWebRequest –](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Přizpůsobí parametry webové žádosti.|  
|[IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Umožňuje Internet Protocol version 6 (IPv6) podporují.|  
|[\<performanceCounter > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Umožňuje síťovým čítače výkonu.|  
|[ServicePointManager –](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Nakonfiguruje připojení k síťovým prostředkům.|  
|[Soket](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Určuje, zda operace soketu používat porty dokončení.|  
|[\<webproxyscript – > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Nakonfiguruje charakteristiky skript používá ke zjišťování webové proxy servery.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
