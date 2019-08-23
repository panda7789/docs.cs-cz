---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942463"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.  
  
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
|name|Určuje název kolekce obslužných rutin tokenu. Pouze hodnoty rozpoznané rozhraním jsou "ActAs" a "OnBehalfOf". Pokud jsou kolekce obslužných rutin tokenů zadány s některým z těchto názvů, kolekce bude použita při zpracování tokenů ActAs nebo OnBehalfOf.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add.md)|Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužných rutin tokenů.|  
|[\<clear>](clear.md)|Vymaže všechny obslužné rutiny tokenů zabezpečení z kolekce obslužných rutin tokenů.|  
|[\<remove>](remove.md)|Odebere obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
  
## <a name="remarks"></a>Poznámky  
 V konfiguraci služby můžete zadat jednu nebo více pojmenovaných obslužných rutin tokenů zabezpečení. Název kolekce můžete zadat pomocí `name` atributu. Jedinými názvy, které rozhraní zpracovává, jsou "ActAs" a "OnBehalfOf". Pokud obslužné rutiny existují v těchto kolekcích, používají se pro službu tokenů zabezpečení (STS) místo výchozích obslužných rutin `ActAs` při `OnBehalfOf` zpracování tokenů.  
  
 Ve výchozím nastavení je kolekce naplněna následujícími typy obslužných rutin <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>: <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Kolekci lze upravit pomocí `<add>` `<clear>` prvků, `<remove>`a. Je nutné zajistit, aby v kolekci existovala pouze jedna obslužná rutina libovolného konkrétního typu. Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy, buď obslužnou rutinu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nebo může být konfigurována v jedné kolekci, ale ne v obou.  
  
 `<securityTokenHandlerConfiguration>` Použijte element k určení nastavení konfigurace obslužných rutin v kolekci. Nastavení zadaná prostřednictvím tohoto elementu přepíší ty zadané ve službě prostřednictvím [ \<elementu IdentityConfiguration >](identityconfiguration.md) . Některé obslužné rutiny (včetně několika vestavěných typů obslužných rutin) mohou podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu. Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadané v kolekci nebo službě.
