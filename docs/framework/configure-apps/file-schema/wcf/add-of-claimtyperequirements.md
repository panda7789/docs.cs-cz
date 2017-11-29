---
title: "&lt;add&gt; – &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dea76ab05c92c009cbb959b8fdba57fd79e2967c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a>&lt;add&gt; – &lt;claimTypeRequirements&gt;
Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje. Například služby stavu požadavky na příchozí přihlašovací údaje, které musí obsahovat sadu typy deklarací identity.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
\<– issuedTokenParameters >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Typ claimType|Identifikátor URI, který definuje typ deklarace identity. Například k nákupu produktu z webu, uživatel musí představovat platná platební karta úvěr dostatečná. Typ deklarace by platební karty identifikátor URI.|  
|isOptional|Logická hodnota, která určuje, zda se pro volitelné deklarace identity. Nastavte tento atribut `false` Pokud to není požadovaná deklarace identity.<br /><br /> Tento atribut můžete použít při služby požádá o některé informace, ale není nutné. Například pokud požadujete, aby uživatel zadal jejich křestní jméno, příjmení a adresa, ale rozhodnout, zda telefonní číslo je volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Určuje kolekci typů požadované deklarace identity.<br /><br /> V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje. Například příchozí pověření musí mít sadu typy deklarací identity. Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.|  
  
## <a name="remarks"></a>Poznámky  
 V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje. Například příchozí pověření musí mít sadu typy deklarací identity. Tento požadavek označované v zásadách zabezpečení. Pokud pověření klienta žádosti od federovaných služby (například CardSpace), vloží požadavků do (třída RequestSecurityToken) žádosti o token tak, aby federované služby můžete vydat přihlašovací údaje, které splňují požadavky odpovídajícím způsobem.  
  
## <a name="example"></a>Příklad  
 Následující konfigurace přidá dva požadavky na typ deklarace identity do vazby zabezpečení.  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
