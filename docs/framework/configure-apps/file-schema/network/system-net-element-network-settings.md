---
title: "&lt;system.Net&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6140a5a66d39cbee3c2a8477dcab88aaa717e745
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a>&lt;system.Net&gt; – Element (nastavení sítě)
Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.  
  
 \<Konfigurace >  
\<System.NET >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[authenticationModules –](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověřování žádostí o Internetu.|  
|[connectionManagement –](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení Internetu hostitele.|  
|[defaultProxy –](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).|  
|[mailSettings –](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).|  
|[requestCaching –](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.|  
|[nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje základní síťové možnosti pro třídy v <xref:System.Net> a související podřízené obory názvů.|  
|[webRequestModules –](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly, které slouží k vyžádání informací z Internetu hostitelů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Konfigurace](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů. Nastavení konfigurace ověřovací moduly, správu připojení, nastavení e-mailu, proxy serveru a moduly požadavek Internetu pro příjem informací z Internetu hostitelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje obvyklá konfigurace používané <xref:System.Net> třídy.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
