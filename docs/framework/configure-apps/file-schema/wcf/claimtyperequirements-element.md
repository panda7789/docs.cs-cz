---
title: Element &lt;claimTypeRequirements&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 187fedc6f81e1cc4a022bfe3b6c68e2c12d09022
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a>Element &lt;claimTypeRequirements&gt;
Určuje kolekci typů požadované deklarace identity.  
  
 V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje. Například příchozí pověření musí mít sadu typy deklarací identity. Každý podřízený element v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.  
  
 Požadavek typ deklarace identity se skládá z identifikátoru URI požadovaného typu deklarace identity v vydaných tokenu společně s určující, zda deklarací identity v vydaný token je vyžadován typ nebo je volitelný parametr typu Boolean.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Možnosti zabezpečení u vlastních vazeb](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
