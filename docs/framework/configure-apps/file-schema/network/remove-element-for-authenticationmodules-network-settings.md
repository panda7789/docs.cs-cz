---
title: <remove> – element pro element authenticationModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: a8afdf442f8dc4e57a407583ea6c452330dae53f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281018"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a>\<Odebrat > – Element pro authenticationModules (nastavení sítě)
Odebere ověřovací modul z aplikace.  
  
 \<Konfigurace >  
\<system.net>  
\<authenticationModules>  
\<remove>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|**type**|Název modulu ověřování k odebrání.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověření síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
 `remove` Element odebere ověřovací moduly, které byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.  
  
 Hodnota `type` atribut by měl být platný název třídy.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere ověřovací modul.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
