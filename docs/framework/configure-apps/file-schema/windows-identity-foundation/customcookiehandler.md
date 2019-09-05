---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252020"
---
# <a name="customcookiehandler"></a>\<customCookieHandler>
Nastaví typ obslužné rutiny vlastního souboru cookie. Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že je atribut elementu "Custom". Vlastní typ musí být odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**  
  
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
|– typ|Určuje vlastní typ, který je odvozen od <xref:System.IdentityModel.Services.CookieHandler> třídy. Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , že používá ke čtení a zápisu souborů cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Když zadáte vlastní obslužnou rutinu souborů cookie nastavením `mode` atributu `<cookieHandler>` elementu na "Custom", je nutné zadat typ obslužné rutiny vlastního `<customCookieHandler>` souboru cookie zahrnutím podřízeného prvku, který odkazuje na typ obslužné rutiny cookie. Tento prvek nelze zadat, pokud `mode` je atribut nastaven na hodnotu "v bloku" nebo "default". Vlastní obslužné rutiny souborů cookie musí <xref:System.IdentityModel.Services.CookieHandler> být odvozeny od třídy.  
  
 Element je reprezentován <xref:System.IdentityModel.Configuration.CustomTypeElement>třídou. `<customCookieHandler>`  
  
## <a name="example"></a>Příklad  
 Následující příklad nakonfiguruje SAM tak, aby používal vlastní obslužnou rutinu cookie `MyNamespace.MyCustomCookieHandler`typu.  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Services.CookieHandler>
