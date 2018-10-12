---
title: '&lt;Přidat&gt; – Element pro bypasslist (nastavení sítě)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b6cf22fcaff928e53c33a8eb4987acd5a7f6250e
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121837"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;Přidat&gt; – Element pro bypasslist (nastavení sítě)
Přidá do seznamu obcházení proxy IP adresu nebo název DNS.  
  
 \<Konfigurace >  
\<system.net>  
\<defaultProxy >  
\<bypasslist – >  
\<add>  
  
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
|**Adresa**|Regulární výraz popisující IP adresu nebo název DNS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[atribut bypasslist bude](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.|  
  
## <a name="remarks"></a>Poznámky  
 `add` Element vloží regulární výrazy popisující IP adresy nebo názvy serverů DNS do seznamu adres, které obcházejí proxy server.  
  
 Hodnota `address` atribut musí být regulární výraz, který popisuje sadu IP adres nebo názvů hostitele.  
  
 Buďte opatrní při zadávání regulární výraz pro tento element. Regulární výraz "[-z] +\\.contoso\\.com" odpovídá některé hostovat v doméně contoso.com, ale také odpovídající libovolného hostitele v doméně contoso.com.cpandl.com. Tak, aby odpovídaly pouze na hostiteli v doméně contoso.com, použijte ukotvení ("$"): "[-z] +\\.contoso\\.com$".  
  
 Další informace o formátování regulárních výrazů naleznete v tématu. [Regulárních výrazech .NET Frameworku](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá do seznamu obcházení dvě adresy. První obcházejí proxy serveru pro všechny servery v doméně contoso.com; druhý vynechá proxy serveru pro všechny servery, IP adresa začíná s 192.168.  
  
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
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
