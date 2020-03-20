---
title: <proxy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154787"
---
# <a name="proxy-element-network-settings"></a>\<prvek> proxy (nastavení sítě)
Definuje proxy server.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

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
|`autoDetect`|Určuje, zda bude server proxy automaticky rozpoznán. Výchozí hodnota je `unspecified`.|  
|`bypassonlocal`|Určuje, zda je proxy server vynechán pro místní prostředky. Mezi místní prostředky patří`http://localhost` `http://loopback`místní `http://127.0.0.1`server ( , ,`http://webserver`nebo ) a identifikátor URI bez tečky ( ). Výchozí hodnota je `unspecified`.|  
|`proxyaddress`|Určuje identifikátor URI proxy serveru, který má být používán.|  
|`scriptLocation`|Určuje umístění konfiguračního skriptu. Nepoužívejte `bypassonlocal` atribut s tímto atributem. |  
|`usesystemdefault`|Určuje, zda se má použít nastavení serveru proxy aplikace Internet Explorer. Pokud je `true`nastavena možnost , následné atributy přepíší nastavení serveru proxy aplikace Internet Explorer. Výchozí hodnota je `unspecified`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[výchozí proxy](defaultproxy-element-network-settings.md)|Konfiguruje proxy server HTTP (HTTP).|  
  
## <a name="text-value"></a>Textová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Prvek `proxy` definuje proxy server pro aplikaci. Pokud tento prvek v konfiguračním souboru chybí, použije rozhraní .NET Framework nastavení serveru proxy v aplikaci Internet Explorer.  
  
 Hodnota atributu `proxyaddress` by měla být dobře tvarovaný indikátor jednotného prostředku (URI).  
  
 Atribut `scriptLocation` odkazuje na automatickou detekci skriptů konfigurace proxy. Třída <xref:System.Net.WebProxy> se pokusí najít konfigurační skript (obvykle s názvem Wpad.dat), pokud je v aplikaci Internet Explorer vybrána možnost **Použít automatický konfigurační skript.** Pokud `bypassonlocal` je nastavena `scriptLocation` na libovolnou hodnotu, je ignorována.
  
 Použijte `usesystemdefault` atribut pro aplikace rozhraní .NET Framework verze 1.1, které migrují na verzi 2.0.  
  
 Výjimka je vyvolána, `proxyaddress` pokud atribut určuje neplatný výchozí proxy server. Vlastnost <xref:System.Exception.InnerException%2A> na výjimce by měl mít další informace o hlavní příčinu chyby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu serveru proxy a obchází proxy server pro místní přístup.  
  
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

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
