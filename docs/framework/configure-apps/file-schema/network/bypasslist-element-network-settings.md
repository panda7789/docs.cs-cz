---
title: <bypasslist> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154943"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> Element (Nastavení sítě)
Obsahuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](add-element-for-bypasslist-network-settings.md)|Přidá adresu IP nebo název DNS do seznamu obejití serveru proxy.|  
|[Jasné](clear-element-for-bypasslist-network-settings.md)|Vymaže seznam bypass.|  
|[Odebrat](remove-element-for-bypasslist-network-settings.md)|Odebere adresu IP nebo název DNS ze seznamu obejití serveru proxy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[výchozí proxy](defaultproxy-element-network-settings.md)|Konfiguruje proxy server HTTP (HTTP).|  
  
## <a name="remarks"></a>Poznámky  
 Seznam obejití obsahuje regulární <xref:System.Net.WebRequest> výrazy, které popisují identifikátory URI, které instancí přistupují přímo namísto prostřednictvím proxy serveru.  
  
 Při zadávání regulárního výrazu pro tento prvek byste měli být opatrní. Regulární výraz "[a-z]+\\\\.contoso .com" odpovídá libovolnému hostiteli v contoso.com doméně, ale také odpovídá libovolnému hostiteli v contoso.com.cpandl.com doméně. Chcete-li porovnat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z]+\\.contoso\\.com$".  
  
 Další informace o regulárních výrazech naleznete v tématu . [Regulární výrazy rozhraní .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá dvě adresy do seznamu bypass. První obchází proxy servery pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery, jejichž IP adresy začínají 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
