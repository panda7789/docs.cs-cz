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
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697683"
---
# <a name="settings-element-network-settings"></a>@no__t – element > 0settings (nastavení sítě)
Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net?displayProperty=nameWithType>.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|Přizpůsobuje parametry používané třídou <xref:System.Net.HttpListener>.|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Přizpůsobuje parametry webového požadavku.|  
|[protokolů](ipv6-element-network-settings.md)|Povolí podporu Internet Protocol verze 6 (IPv6).|  
|[@no__t – element > 1performanceCounter (nastavení sítě)](performancecounter-element-network-settings.md)|Povolí čítače výkonu sítě.|  
|[Třída ServicePointManager](servicepointmanager-element-network-settings.md)|Nakonfiguruje připojení k síťovým prostředkům.|  
|[zásuvky](socket-element-network-settings.md)|Určuje, jestli operace soketu používají porty dokončení.|  
|[@no__t – element > 1webProxyScript (nastavení sítě)](webproxyscript-element-network-settings.md)|Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
