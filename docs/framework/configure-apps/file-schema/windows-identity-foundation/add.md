---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73973806"
---
# \<add>
Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
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
|typ|Název typu CLR obslužné rutiny tokenu, která má být přidána. Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|Poskytuje volitelnou konfiguraci pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 `<add>`Element může převzít jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu. To závisí na tom, zda třída obslužné rutiny, na kterou odkazuje `type` atribut `<add>` elementu, poskytuje podporu pro tuto funkci. Třídy obslužné rutiny tokenu, které poskytují tuto funkci, musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objekt.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Tuto funkci poskytují některé z vestavěných tříd obslužné rutiny tokenů zabezpečení. Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,, a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .  
  
> [!IMPORTANT]
> Kolekce obslužných rutin tokenů může obsahovat pouze jednu obslužnou rutinu pro daný typ. To znamená, že pokud chcete přidat obslužnou rutinu, která je odvozena od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy do kolekce, musíte nejprve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> z kolekce odebrat, která je ve výchozím nastavení přítomna. Pomocí [\<remove>](remove.md) elementu můžete odebrat jednu obslužnou rutinu z kolekce nebo použít [\<clear>](clear.md) element k odebrání všech obslužných rutin z kolekce.  
  
 Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadaná v kolekci obslužných rutin tokenu v rámci [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu a na úrovni služby určené v rámci [\<identityConfiguration>](identityconfiguration.md) elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje použití `<add>` `<remove>` elementů a k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace. KÓD XML je získán z `ClaimsAwareWebFarm` ukázky.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
