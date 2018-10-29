---
title: '&lt;system.Net&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 82e022e28d3559791be3236fb80081807426a456
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192535"
---
# <a name="ltsystemnetgt-element-network-settings"></a>&lt;system.Net&gt; – Element (nastavení sítě)
Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.  
  
 \<Konfigurace >  
\<system.net>  
  
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
|[authenticationModules –](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověření požadavků na Internetu.|  
|[connectionManagement –](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostiteli, který Internet.|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).|  
|[mailSettings –](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).|  
|[requestCaching –](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro třídy v <xref:System.Net> a související podřízené obory názvů.|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly, které slouží k vyžádání informací z Internetu hostitelů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Konfigurace](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 [ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů. Nastavení konfigurace modulů ověřování, Správa připojení, nastavení pošty, proxy server a Internetu žádost moduly pro příjem informací z Internetu hostitelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje typickou konfiguraci používané <xref:System.Net> třídy.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
