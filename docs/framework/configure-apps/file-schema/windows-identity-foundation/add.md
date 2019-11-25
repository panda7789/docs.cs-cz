---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973806"
---
# <a name="add"></a>\<přidat >
Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**  
  
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
|– typ|Název typu CLR obslužné rutiny tokenu, která má být přidána. Další informace o tom, jak zadat atribut `type`, naleznete v tématu [odkazy na vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.|  
|[\<sessionTokenRequirement >](sessiontokenrequirement.md)|Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> nebo odvozené třídy.|  
|[\<userNameSecurityTokenHandlerRequirement >](usernamesecuritytokenhandlerrequirement.md)|Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nebo odvozené třídy.|  
|[\<x509SecurityTokenHandlerRequirement >](x509securitytokenhandlerrequirement.md)|Poskytuje volitelnou konfiguraci pro třídu <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> nebo odvozené třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](securitytokenhandlers.md)|Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Element `<add>` může převzít jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu. To závisí na tom, zda třída obslužné rutiny, na kterou odkazuje atribut `type` elementu `<add>`, poskytuje podporu pro tuto funkci. Třídy obslužné rutiny tokenu, které poskytují tuto funkci, musí vystavit konstruktor, který přebírá objekt <xref:System.Xml.XmlElement>.  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 Tuto funkci poskytují některé z vestavěných tříd obslužné rutiny tokenů zabezpečení. Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
> Kolekce obslužných rutin tokenů může obsahovat pouze jednu obslužnou rutinu pro daný typ. To znamená, že pokud chcete přidat obslužnou rutinu, která je odvozena od třídy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> do kolekce, je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, která je ve výchozím nastavení přítomna, z kolekce. Pomocí elementu [\<remove >](remove.md) můžete z kolekce odebrat jednu obslužnou rutinu nebo pomocí elementu [\<vymazat >](clear.md) odstranit všechny obslužné rutiny z kolekce.  
  
 Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadaná v kolekci obslužných rutin tokenu v rámci [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) elementu a na úrovni služby v rámci elementu [\<IdentityConfiguration >](identityconfiguration.md) .  
  
## <a name="example"></a>Příklad  
 Následující kód XML ukazuje použití prvků `<add>` a `<remove>` k nahrazení výchozí obslužné rutiny tokenu relace s vlastní obslužnou rutinou tokenu relace. KÓD XML je pořízen z ukázky `ClaimsAwareWebFarm`.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
