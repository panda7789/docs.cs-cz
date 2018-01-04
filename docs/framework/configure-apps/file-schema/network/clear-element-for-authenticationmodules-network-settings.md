---
title: "&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b1c27ba6cdae88a36813dcf67ffc386c94403c1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a>&lt;Vymazat&gt; Element pro authenticationModules – (nastavení sítě)
Vymaže všechny moduly ověřování z aplikace.  
  
 \<Konfigurace >  
\<System.NET >  
\<authenticationModules – >  
\<Clear >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[authenticationModules –](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověřování žádostí o síti.|  
  
## <a name="remarks"></a>Poznámky  
 `clear` Element odebere všechny ověřovací moduly, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny moduly nakonfigurované ověřování.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
