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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154787"
---
# <a name="proxy-element-network-settings"></a>\<proxy> – element (nastavení sítě)
Definuje proxy server.  

[**\<configuration>**](../configuration-element.md)\
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
|`autoDetect`|Určuje, jestli se proxy server automaticky detekuje. Výchozí hodnota je `unspecified`.|  
|`bypassonlocal`|Určuje, jestli se proxy server pro místní prostředky obejít. Místní prostředky zahrnují místní server ( `http://localhost` , `http://loopback` , nebo `http://127.0.0.1` ) a identifikátor URI bez tečky ( `http://webserver` ). Výchozí hodnota je `unspecified`.|  
|`proxyaddress`|Určuje identifikátor URI proxy serveru, který se má použít.|  
|`scriptLocation`|Určuje umístění konfiguračního skriptu. Nepoužívejte `bypassonlocal` atribut s tímto atributem. |  
|`usesystemdefault`|Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer. Pokud je nastaveno na `true` , budou následující atributy přepsat nastavení proxy serveru aplikace Internet Explorer. Výchozí hodnota je `unspecified`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Textová hodnota  
  
## <a name="remarks"></a>Poznámky  
 `proxy`Prvek definuje proxy server pro aplikaci. Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.  
  
 Hodnota `proxyaddress` atributu musí být ve správném formátu (Uniform Resource).  
  
 `scriptLocation`Atribut odkazuje na automatické zjišťování skriptů konfigurace proxy serveru. <xref:System.Net.WebProxy>Třída se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v aplikaci Internet Explorer vybraná možnost **použít skript automatické konfigurace** . Pokud `bypassonlocal` je nastavená na libovolnou hodnotu, `scriptLocation` ignoruje se.
  
 Použijte `usesystemdefault` atribut pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.  
  
 Pokud `proxyaddress` atribut specifikuje neplatný výchozí proxy server, je vyvolána výjimka. <xref:System.Exception.InnerException%2A>Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup.  
  
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
