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
ms.openlocfilehash: 5f327a2bb4fe316497614f14669907d514c20654
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089196"
---
# <a name="proxy-element-network-settings"></a>\<> elementu proxy serveru (nastavení sítě)
Definuje proxy server.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<proxy >**

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
|`bypassonlocal`|Určuje, jestli se proxy server pro místní prostředky obejít. Místní prostředky zahrnují místní server (`http://localhost`, `http://loopback` nebo `http://127.0.0.1`) a identifikátor URI bez tečky (`http://webserver`). Výchozí hodnota je `unspecified`.|  
|`proxyaddress`|Určuje identifikátor URI proxy serveru, který se má použít.|  
|`scriptLocation`|Určuje umístění konfiguračního skriptu. Nepoužívejte atribut `bypassonlocal` s tímto atributem. |  
|`usesystemdefault`|Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer. Pokud je nastavená na `true`, následné atributy přepíšou nastavení proxy serveru aplikace Internet Explorer. Výchozí hodnota je `unspecified`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Textová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Element `proxy` definuje proxy server pro aplikaci. Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.  
  
 Hodnota atributu `proxyaddress` musí být ve správném formátu (Uniform Resource).  
  
 Atribut `scriptLocation` odkazuje na automatické zjišťování skriptů konfigurace proxy serveru. Třída <xref:System.Net.WebProxy> se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v Internet Exploreru vybraná možnost **použít skript pro automatickou konfiguraci** . Pokud je `bypassonlocal` nastavená na libovolnou hodnotu, `scriptLocation` se ignoruje.
  
 Použijte atribut `usesystemdefault` pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.  
  
 Pokud atribut `proxyaddress` určuje neplatný výchozí proxy server, je vyvolána výjimka. Vlastnost <xref:System.Exception.InnerException%2A> výjimky by měla obsahovat další informace o hlavní příčině chyby.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
