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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154553"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> element (nastavení sítě)
Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
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
|[autentizační moduly](authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověřování požadavků sítě Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k hostiteli sítě Internet.|  
|[výchozí proxy](defaultproxy-element-network-settings.md)|Konfiguruje proxy server HTTP (HTTP).|  
|[mailNastavení](mailsettings-element-network-settings.md)|Konfiguruje možnosti odesílání pošty protokolu SMTP (SMTP) protokolu SMTP.|  
|[requestCaching](requestcaching-element-network-settings.md)|Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.|  
|[zdroje dat](settings-element-network-settings.md)|Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> a souvisejícípodřízené názvobory.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Určuje moduly, které mají být používány k vyžádání informací od hostitelů v Síti Internet.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Konfigurace](../configuration-element.md)|Obsahuje nastavení pro všechny obory názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek [ \<system.net>](system-net-element-network-settings.md) obsahuje nastavení <xref:System.Net> pro třídy v a související podřízené obory názvů. Nastavení konfigurují ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly požadavků na Internet pro příjem informací z hostitelů sítě Internet.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje typickou <xref:System.Net> konfiguraci používanou třídami.  
  
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

- [Schéma nastavení sítě](index.md)
