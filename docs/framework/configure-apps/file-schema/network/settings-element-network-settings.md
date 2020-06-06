---
title: <settings> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089107"
---
# <a name="settings-element-network-settings"></a>\<settings> – element (nastavení sítě)
Nakonfiguruje základní možnosti sítě pro <xref:System.Net?displayProperty=nameWithType> obor názvů.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Přizpůsobuje parametry webového požadavku.|  
|[protokolů](ipv6-element-network-settings.md)|Povolí podporu Internet Protocol verze 6 (IPv6).|  
|[\<performanceCounter>– Element (nastavení sítě)](performancecounter-element-network-settings.md)|Povolí čítače výkonu sítě.|  
|[Třída ServicePointManager](servicepointmanager-element-network-settings.md)|Nakonfiguruje připojení k síťovým prostředkům.|  
|[zásuvky](socket-element-network-settings.md)|Určuje, jestli operace soketu používají porty dokončení.|  
|[\<webProxyScript>– Element (nastavení sítě)](webproxyscript-element-network-settings.md)|Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
