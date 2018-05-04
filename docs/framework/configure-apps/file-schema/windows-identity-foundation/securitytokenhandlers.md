---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 16827aa774a8a76f16106a8650423d0d7f084982
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
  
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
|name|Určuje název kolekce obslužná rutina tokenu. Jsou pouze hodnoty rozpoznáno rozhraní "ActAs" a "OnBehalfOf". Pokud obslužná rutina tokenu kolekce jsou zadané s některou z těchto názvů, kolekce se použije při zpracování ActAs nebo prostřednictvím profilu OnBehalfOf tokeny v uvedeném pořadí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Obslužná rutina tokenu zabezpečení se přidá do kolekce obslužná rutina tokenu.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Vymaže všechny rutiny tokenu zabezpečení z kolekce obslužná rutina tokenu.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Obslužná rutina tokenu zabezpečení se odebere z kolekce obslužná rutina tokenu.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Poskytuje konfigurace pro kolekci tokenu obslužné rutiny.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identity úrovně služeb.|  
  
## <a name="remarks"></a>Poznámky  
 V konfiguraci služby můžete zadat jednu nebo více pojmenované kolekcí obslužných rutin, token zabezpečení. Můžete zadat název pro kolekci pomocí `name` atribut. Pouze názvy, které zpracovává rozhraní jsou "ActAs" a "OnBehalfOf". Pokud v těchto kolekcích existuje obslužné rutiny, použijí se pomocí služby tokenů zabezpečení (STS) namísto výchozí obslužné rutiny při zpracování `ActAs` a `OnBehalfOf` tokeny.  
  
 Ve výchozím nastavení, je kolekce naplněný následující typy obslužných rutin: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Kolekce můžete upravit pomocí `<add>`, `<remove>`, a `<clear>` elementy. Je nutné zajistit, že pouze jeden obslužná rutina žádný konkrétní typ v kolekci existuje. Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy buď vaší obslužné rutiny nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> může být nakonfigurována v jedné kolekci, ale ne obojí.  
  
 Použití `<securityTokenHandlerConfiguration>` element ke specifikaci nastavení konfigurace pro obslužné rutiny, v kolekci. Nastavení zadána prostřednictvím tohoto elementu přepíšou zadaný u služby pomocí [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element. Některé obslužné rutiny (včetně několik typů předdefinované obslužné rutiny) může podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu. Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci nebo službu.
