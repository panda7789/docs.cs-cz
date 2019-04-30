---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: a5af3893ab72d23c2b3814569decfc50431b8e55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793832"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Určuje název kolekce obslužné rutiny tokenů. Pouze hodnoty rozpoznán v rámci rozhraní jsou "ActAs" a "Prostřednictvím profilu OnBehalfOf". Pokud s některou z těchto názvů jsou zadané obslužné rutiny tokenů kolekce, kolekce se použije při zpracování ActAs nebo OnBehalfOf tokeny v uvedeném pořadí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Vymaže všechny obslužné rutiny tokenů zabezpečení z kolekce obslužné rutiny tokenů.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Odebere obslužnou rutinu tokenu zabezpečení z kolekce obslužné rutiny tokenů.|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužné rutiny tokenů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identit na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 V konfiguraci služby můžete zadat jednu nebo více pojmenovaný kolekcí obslužné rutiny tokenů zabezpečení. Můžete zadat název pro kolekci pomocí `name` atribut. Pouze názvy, které rozhraní zpracovává jsou "ActAs" a "Prostřednictvím profilu OnBehalfOf". Pokud obslužných rutin v těchto kolekcích, používají se pomocí služby tokenů zabezpečení (STS) namísto výchozích obslužných rutin při zpracování `ActAs` a `OnBehalfOf` tokeny.  
  
 Ve výchozím nastavení, kolekce se vyplní následující typy obslužných rutin: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Kolekce můžete upravit pomocí `<add>`, `<remove>`, a `<clear>` elementy. Musíte zajistit, že v kolekci existuje pouze jedna obslužná rutina určitého typu. Například, pokud jsou odvozeny z obslužné rutiny <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy buď vaše obslužná rutina nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> se dá nakonfigurovat v jedné kolekce, ale ne obojí.  
  
 Použití `<securityTokenHandlerConfiguration>` element k určení nastavení konfigurace pro obslužné rutiny v kolekci. Bylo nastaveno prostřednictvím tohoto prvku mají přednost před akcemi zadané na této služby prostřednictvím [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Některé obslužné rutiny (včetně několik typů integrovaných obslužná rutina) může podporovat další konfiguraci prostřednictvím podřízený prvek `<add>` elementu. Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci nebo službu.
