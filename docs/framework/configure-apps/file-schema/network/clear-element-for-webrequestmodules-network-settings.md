---
title: "&lt;Vymazat&gt; Element pro webRequestModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 34a814c14cc482bdf5deafceebae253da921736b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a>&lt;Vymazat&gt; Element pro webRequestModules – (nastavení sítě)
Odebere všechny registrované moduly žádost webové aplikace.  
  
 \<Konfigurace >  
\<System.NET >  
\<webRequestModules – >  
\<Clear >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules –](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly sloužící k požadavku na informace z hostitelů v síti.|  
  
## <a name="remarks"></a>Poznámky  
 `clear` Element odebere všechny registrované moduly webové žádosti, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad vymaže všechny moduly webové žádosti a pak zaregistruje modul webové žádosti pro protokol HTTP.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebRequest>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
