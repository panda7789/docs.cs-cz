---
title: <module> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154826"
---
# <a name="module-element-network-settings"></a>\<modul> Element (Nastavení sítě)
Přidá do aplikace nový proxy modul.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>modulu**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`type`|Plně kvalifikovaný název typu (označený <xref:System.Type.FullName%2A> vlastností) a název sestavení <xref:System.Reflection.Assembly.FullName%2A> (označený vlastností), oddělený čárkou, který implementuje proxy server.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[výchozí proxy](defaultproxy-element-network-settings.md)|Konfiguruje proxy server HTTP (HTTP).|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `module` registruje proxy třídy, které implementují <xref:System.Net.IWebProxy> rozhraní. Po registraci třídy `module` proxy lze požádat o informace prostřednictvím podporovaného proxy serveru.  
  
 Hodnotou atributu `type` by měl být název třídy modulu a název odpovídající knihovny dynamických odkazů (DLL).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje vlastní třídu proxy.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
