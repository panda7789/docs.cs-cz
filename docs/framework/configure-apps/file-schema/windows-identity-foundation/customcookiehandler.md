---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 61b128d5856fd8e35516949b637177dc38a17164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
Nastaví typ obslužné rutiny vlastní soubor cookie. Tento element může být pouze existuje-li `mode` atribut `<cookieHandler>` element je "Vlastní". Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<customCookieHandler >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Určuje vlastního typu, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy. Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> používá ke čtení a zápis souborů cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte vlastní soubor cookie obslužnou rutinu nastavením `mode` atribut `<cookieHandler>` element na "Vlastní", je třeba zadat typ obslužné rutiny vlastní soubor cookie zahrnutím `<customCookieHandler>` podřízený element, který odkazuje na typ obslužné rutiny souborů cookie. Tento element nemůže být zadán, kdy `mode` atributu je nastavena na "Chunked" nebo "Výchozí". Vlastní soubor cookie obslužné rutiny musí být odvozeny od <xref:System.IdentityModel.Services.CookieHandler> třídy.  
  
 `<customCookieHandler>` Element je reprezentována <xref:System.IdentityModel.Configuration.CustomTypeElement> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfiguruje SAM použít vlastní soubor cookie obslužnou rutinu typu `MyNamespace.MyCustomCookieHandler`.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.CookieHandler>
