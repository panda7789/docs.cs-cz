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
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154969"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModuly> element (nastavení sítě)
Určuje moduly používané k ověřování síťových požadavků.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<autentizační moduly>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](add-element-for-authenticationmodules-network-settings.md)|Přidá do aplikace ověřovací modul.|  
|[Jasné](clear-element-for-authenticationmodules-network-settings.md)|Vymaže všechny ověřovací moduly z aplikace.|  
|[Odebrat](remove-element-for-authenticationmodules-network-settings.md)|Odebere ověřovací modul z aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `authenticationModule` určuje ověřovací moduly, které provádějí proces ověřování se serverem. Ověřovací modul musí <xref:System.Net.IAuthenticationModule> implementovat rozhraní.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad umožňuje ověřovací modul. Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schéma nastavení sítě](index.md)
