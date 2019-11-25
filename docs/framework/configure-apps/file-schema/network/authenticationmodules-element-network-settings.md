---
title: <authenticationModules> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: bacaaf92464a355804a9ea8307f6e6f1caac1f05
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087616"
---
# <a name="authenticationmodules-element-network-settings"></a>\<element > authenticationModules (nastavení sítě)
Určuje moduly používané pro ověřování síťových požadavků.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<authenticationModules >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-authenticationmodules-network-settings.md)|Přidá do aplikace modul ověřování.|  
|[jejich](clear-element-for-authenticationmodules-network-settings.md)|Vymaže všechny moduly ověřování z aplikace.|  
|[remove](remove-element-for-authenticationmodules-network-settings.md)|Odebere ověřovací modul z aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Element `authenticationModule` Určuje moduly ověřování, které provádí proces ověřování se serverem. Ověřovací modul musí implementovat rozhraní <xref:System.Net.IAuthenticationModule>.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad povoluje ověřovací modul. Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schéma nastavení sítě](index.md)
