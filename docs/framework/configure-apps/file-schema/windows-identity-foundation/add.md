---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddbf1b822550876d849f830d80cff9a74311ba9c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506771"
---
# <a name="ltaddgt"></a>&lt;add&gt;
Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
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
|– typ|Název typu CLR přidat obslužnou rutinu tokenu. Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.|  
|[\<sessionTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy nebo odvozené třídy.|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídy nebo odvozené třídy.|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídy nebo odvozené třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.|  
  
## <a name="remarks"></a>Poznámky  
 `<add>` Element může trvat jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu. Toto je závislá na Určuje, zda třída obslužné rutiny odkazuje prostřednictvím `type` atribut `<add>` element poskytuje podporu pro tuto funkci. Třídy obslužné rutiny tokenů, které poskytují tuto funkci musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objektu.  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Několik tříd obslužné rutiny tokenů integrované zabezpečení poskytují tuto funkci. Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  Obslužná rutina tokenů kolekce může obsahovat jenom jedna obslužná rutina daného typu. To znamená, například, že pokud chcete přidat obslužnou rutinu, která je odvozena z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy do kolekce, musíte nejdřív odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, což je k dispozici ve výchozím nastavení, z kolekce. Můžete použít [ \<odebrat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) prvek, který chcete odebrat z kolekce nebo použití jedna obslužná rutina [ \<vymazat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) prvek, který chcete odebrat všechny obslužné rutiny z kolekce.  
  
 Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci obslužné rutiny tokenů v části [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element a jsou uvedeny na úrovni služby v části [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje použití `<add>` a `<remove>` prvků, které mají výchozí obslužnou rutinu tokenu relace nahraďte obslužnou rutinu tokenu relace. XML je převzata z `ClaimsAwareWebFarm` vzorku.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
