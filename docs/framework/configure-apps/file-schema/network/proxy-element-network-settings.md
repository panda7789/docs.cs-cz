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
ms.openlocfilehash: a183c4160c4cd55b05c5c23f7a10e3a1d1c74ea4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659292"
---
# <a name="proxy-element-network-settings"></a>\<> – element proxy (nastavení sítě)
Definuje proxy server.  
  
 \<> Konfigurace  
\<system.net>  
\<defaultProxy>  
\<proxy>  
  
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
|`bypassonlocal`|Určuje, jestli se proxy server pro místní prostředky obejít. Místní prostředky zahrnují místní server`http://localhost`(, `http://loopback`, nebo `http://127.0.0.1`) a identifikátor URI bez tečky (`http://webserver`). Výchozí hodnota je `unspecified`.|  
|`proxyaddress`|Určuje identifikátor URI proxy serveru, který se má použít.|  
|`scriptLocation`|Určuje umístění konfiguračního skriptu. Nepoužívejte `bypassonlocal` atribut s tímto atributem. |  
|`usesystemdefault`|Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer. Pokud je nastaveno `true`na, budou následující atributy přepsat nastavení proxy serveru aplikace Internet Explorer. Výchozí hodnota je `unspecified`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Textová hodnota  
  
## <a name="remarks"></a>Poznámky  
 `proxy` Prvek definuje proxy server pro aplikaci. Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.  
  
 Hodnota `proxyaddress` atributu musí být ve správném formátu (Uniform Resource).  
  
 `scriptLocation` Atribut odkazuje na automatické zjišťování skriptů konfigurace proxy serveru. Třída se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v aplikaci Internet Explorer vybraná možnost **použít skript automatické konfigurace.** <xref:System.Net.WebProxy> Pokud `bypassonlocal` je nastavená na libovolnou hodnotu `scriptLocation` , ignoruje se.
  
 `usesystemdefault` Použijte atribut pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.  
  
 Pokud `proxyaddress` atribut specifikuje neplatný výchozí proxy server, je vyvolána výjimka. <xref:System.Exception.InnerException%2A> Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.  
  
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
