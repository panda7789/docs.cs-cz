---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755757"
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Zaregistruje překladač tokenu služby, který je používán obslužné rutiny v kolekci obslužná rutina tokenu. Překladač tokenu služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Určuje typ tokenu překladače služby. Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu nebo typu, která je odvozena z <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy. Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na vlastní typ]. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.|  
  
## <a name="remarks"></a>Poznámky  
 Překladač tokenu služby lze použít k vyřešení šifrování tokenu na příchozí tokeny a zprávy. Umožňuje načíst klíč, který se má použít k dešifrování tokenů, příchozí. Je nutné zadat `type` atribut. Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.  
  
 Některé tokenu obslužné rutiny umožňují určit nastavení tokenu překladače služby v konfiguraci. Nastavení na jednotlivých tokenu obslužné rutiny potlačit platformám zadaným v kolekci obslužná rutina tokenu zabezpečení.  
  
> [!NOTE]
>  Určení `<serviceTokenResolver>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu. Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
