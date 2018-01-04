---
title: "&lt;Odebrat&gt; Element pro authenticationModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 077a6f3cb7020d501978fa112a0c318efee27e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a>&lt;Odebrat&gt; Element pro authenticationModules – (nastavení sítě)
Odebere modul ověřování z aplikace.  
  
 \<Konfigurace >  
\<System.NET >  
\<authenticationModules – >  
\<Odebrat >  
  
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
|**Typ**|Název modulu ověřování odebrat.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[authenticationModules –](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Určuje moduly používané k ověřování žádostí o síti.|  
  
## <a name="remarks"></a>Poznámky  
 `remove` Element odebere ověřovací moduly, které byly dříve definované v konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurace.  
  
 Hodnota `type` atribut by měl být platný název třídy.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere modul ověřování.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
