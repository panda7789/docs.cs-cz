---
title: "&lt;webproxyscript –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a>&lt;webproxyscript –&gt; – Element (nastavení sítě)
Nakonfiguruje charakteristiky skript používá ke zjišťování webové proxy servery.  
  
 \<Konfigurace >  
\<System.NET >  
\<Nastavení >  
\<webproxyscript – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`downloadTimeout`|Určuje maximální dobu se stáhnout skript v hodiny, minuty a sekundy. Výchozí hodnota je jedna minuta.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
