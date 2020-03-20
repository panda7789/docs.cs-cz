---
title: <add> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155074"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<přidat> element pro bypasslist (Nastavení sítě)
Přidá adresu IP nebo název DNS do seznamu obejití serveru proxy.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|**Adresu**|Regulární výraz popisující adresu IP nebo název DNS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Bypasslist](bypasslist-element-network-settings.md)|Obsahuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `add` vloží regulární výrazy popisující adresy IP nebo názvy serverů DNS do seznamu adres, které obcházejí proxy server.  
  
 Hodnota atributu `address` by měla být regulární výraz, který popisuje sadu ADRES IP nebo názvů hostitelů.  
  
 Při zadávání regulárního výrazu pro tento prvek byste měli být opatrní. Regulární výraz "[a-z]+\\\\.contoso .com" odpovídá libovolnému hostiteli v contoso.com doméně, ale také odpovídá libovolnému hostiteli v contoso.com.cpandl.com doméně. Chcete-li porovnat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z]+\\.contoso\\.com$".  
  
 Další informace o regulárních výrazech naleznete v tématu . [Regulární výrazy rozhraní .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá dvě adresy do seznamu bypass. První obchází proxy servery pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery, jejichž IP adresa začíná 192.168.  
  
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
