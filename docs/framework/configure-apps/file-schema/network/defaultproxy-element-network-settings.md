---
title: "&lt;defaultProxy –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d0b09f5c845fc9a18c2a1dd919272c2924478eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy –&gt; – Element (nastavení sítě)
Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).  
  
 \<Konfigurace >  
\<System.NET >  
\<defaultProxy – >  
  
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
|`enabled`|Určuje, jestli se používá webový proxy server. Výchozí hodnota je `true`.|  
|`useDefaultCredentials`|Určuje, jestli jsou pro přístup k proxy serveru webové používá výchozí pověření pro tohoto hostitele. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[bypasslist –](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy serveru.|  
|[modul](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Přidá nový modul proxy serveru k aplikaci.|  
|[proxy server](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Definuje proxy server.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud defaultProxy – element není prázdný, použije se nastavení proxy serveru z Internet Exploreru. Toto chování se liší od rozhraní .NET Framework verze 1.1.  
  
 Je vyvolána výjimka, pokud [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element určuje typ neveřejný, typ není odvozování z <xref:System.Net.IWebProxy> třídu, došlo k výjimce z výchozí konstruktor tohoto objektu, nebo došlo k výjimce při načítání systému zadat výchozí proxy server. <xref:System.Exception.InnerException%2A> Vlastnost výjimky by měl mít další informace o hlavních příčin této chyby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
