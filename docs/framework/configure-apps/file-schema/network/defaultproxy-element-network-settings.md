---
title: '&lt;defaultProxy&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c1783776b62532a2bd28067ca9bdb6ae4c80c717
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400319"
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy&gt; – Element (nastavení sítě)
Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).  
  
 \<Konfigurace >  
\<system.net>  
\<defaultProxy >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|`enabled`|Určuje, zda se používá webový proxy server. Výchozí hodnota je `true`.|  
|`useDefaultCredentials`|Určuje, zda výchozí přihlašovací údaje pro tohoto hostitele se používají pro přístup webový proxy server. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[atribut bypasslist bude](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.|  
|[Modul](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Přidá nový modul proxy serveru do aplikace.|  
|[Proxy server](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Definuje proxy server.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud defaultProxy – element je prázdný, použije se nastavení proxy serveru z aplikace Internet Explorer. Toto chování se liší od verze 1.1 rozhraní .NET Framework.  
  
 Pokud je vyvolána výjimka [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) prvek určuje neveřejný typ, typ není odvozený od <xref:System.Net.IWebProxy> došlo k výjimce z výchozího konstruktoru tohoto objektu třídy, nebo došlo k výjimce při načítání systému zadat výchozí proxy server. <xref:System.Exception.InnerException%2A> Vlastnosti výjimky by měl mít další informace o hlavní příčinu chyby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup a contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
