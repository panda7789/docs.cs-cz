---
title: '&lt;add&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d863a0fc2b575aceef12370a57f7f7807261cb5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt"></a>&lt;add&gt;
Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Název typu CLR obslužná rutina tokenu má být přidán. Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Poskytuje konfigurace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , nebo odvozená třída buď z těchto tříd.|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|Obsahuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|Obsahuje konfiguraci <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.|  
  
## <a name="remarks"></a>Poznámky  
 `<add>` Element může trvat jeden podřízený element, který určuje konfiguraci, aby obslužná rutina tokenu. Toto je závislá na tom, jestli třídu obslužné rutiny odkazuje prostřednictvím `type` atribut `<add>` element poskytuje podporu pro tuto funkci. Obslužná rutina tokenu třídy, které poskytují tuto funkci musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objektu.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Několik tříd obslužná rutina tokenu integrované zabezpečení zadejte tuto funkci. Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  Obslužná rutina tokenu kolekce může obsahovat jenom jeden obslužné rutině daného typu. To znamená, například, pokud chcete přidat obslužnou rutinu, která je odvozená od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> – třída do kolekce, je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, což je existuje ve výchozím nastavení, z kolekce. Můžete použít [ \<odebrat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elementu, který chcete odebrat z kolekce nebo použijte jeden obslužné rutině [ \<clear >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu, který chcete odebrat všechny rutiny z kolekce.  
  
 Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci obslužná rutina tokenu v [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu a uvedenými na úrovni služby, v části [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje použití `<add>` a `<remove>` elementy nahradit výchozí obslužnou rutinu tokenu relace obslužnou rutinu tokenu vlastní relaci. Soubor XML je převzat ze `ClaimsAwareWebFarm` ukázka.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
