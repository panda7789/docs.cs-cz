---
title: "&lt;proxy&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b0b397e66e0f73d10f482bc9151a6fbacf3e774d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltproxygt-element-network-settings"></a>&lt;proxy&gt; – Element (nastavení sítě)
Definuje proxy server.  
  
 \<Konfigurace >  
\<System.NET >  
\<defaultProxy – >  
\<proxy >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`autoDetect`|Určuje, zda je automaticky zjišťován proxy serveru. Výchozí hodnota je `unspecified`.|  
|`bypassonlocal`|Určuje, zda je u místních prostředků název proxy serveru. Místní prostředky zahrnují URI bez tečky (http://webserver) a na místním serveru (http://localhost, http://loopback nebo http://127.0.0.1). Výchozí hodnota je `unspecified`.|  
|`proxyaddress`|Určuje identifikátor URI k použití proxy serveru.|  
|`scriptLocation`|Určuje umístění konfigurační skript.|  
|`usesystemdefault`|Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer. Pokud nastavena na `true`, následující atributy se přepíše nastavení proxy serveru aplikace Internet Explorer. Výchozí hodnota je `unspecified`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy –](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).|  
  
## <a name="text-value"></a>Textová hodnota  
  
## <a name="remarks"></a>Poznámky  
 `proxy` Element definuje proxy server pro aplikaci. Pokud tento element chybí z konfiguračního souboru, potom rozhraní .NET Framework bude používat nastavení proxy serveru v Internet Exploreru.  
  
 Hodnota `proxyaddress` atribut by měl mít ve správném formátu indikátor URI (Uniform Resource).  
  
 `scriptLocation` Atribut odkazuje na automatické zjišťování proxy konfigurační skripty. <xref:System.Net.WebProxy> Třídy se pokusí najít konfigurační skript (obvykle s názvem Wpad.dat) Pokud **použít automatický konfigurační skript** v aplikaci Internet Explorer je vybraná možnost.  
  
 Použití `usesystemdefault` atribut pro rozhraní .NET Framework verze 1.1 aplikace, které provádíte migraci do verze 2.0.  
  
 Pokud je vyvolána výjimka `proxyaddress` atribut určuje neplatná výchozí proxy server. <xref:System.Exception.InnerException%2A> Vlastnost výjimky by měl mít další informace o hlavních příčin této chyby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
