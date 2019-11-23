---
title: <system.Net> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697506"
---
# <a name="systemnet-element-network-settings"></a>\<– element > systému .NET (nastavení sítě)
Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. net >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Určuje moduly používané pro ověřování internetových požadavků.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostiteli v Internetu.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).|  
|[requestCaching](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[možnost](settings-element-network-settings.md)|Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> a související podřízené obory názvů.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Určuje moduly, které se použijí k vyžádání informací od hostitelů v Internetu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[rozšířeného](../configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Element [\<System. net >](system-net-element-network-settings.md) obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů. Nastavení konfigurovat ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly internetových požadavků pro příjem informací z internetových hostitelů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje typickou konfiguraci, kterou používá <xref:System.Net> třídy.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení sítě](index.md)
