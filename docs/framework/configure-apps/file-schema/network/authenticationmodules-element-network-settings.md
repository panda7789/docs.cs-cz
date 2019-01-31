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
ms.openlocfilehash: 1e40ee4a0bb0731c78d27b7ba9994884ef9ff447
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271587"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules – > – Element (nastavení sítě)
Určuje moduly používané k ověření síťové požadavky.  
  
 \<Konfigurace >  
\<system.net>  
\<authenticationModules>  
  
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
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|Přidá modul ověřování do aplikace.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|Vymaže všechny moduly ověřování z aplikace.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|Odebere ověřovací modul z aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 `authenticationModule` Prvek určuje moduly ověřování, které provádí proces ověřování se serverem. Ověřovací modul musí implementovat <xref:System.Net.IAuthenticationModule> rozhraní.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad povolí ověřovací modul. Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
