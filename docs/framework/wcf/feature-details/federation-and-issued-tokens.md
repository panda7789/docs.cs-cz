---
title: "Federace a vystavené tokeny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05a110318bbe92f18d0bc6becb453a5d7851821c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="federation-and-issued-tokens"></a>Federace a vystavené tokeny
S [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], můžete vytvořit klientů komunikujících bezpečně s služby, které implementují specifikace WS-Federation a WS-Trust. Specifikace poskytnout mechanismy, které umožňují ověřování a autorizace mezi různé důvěryhodnosti sfér pomocí XML, protokolu SOAP a webové služby popis Language (WSDL).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 Obsahuje přehled federace.  
  
 [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Jsou uvedené problémy návrhu znát při vytvoření federovaného služby nebo klientů.  
  
 [Postupy: vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Popisuje základní informace o vytvoření federovaného klienta s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Popisuje kroky k vytvoření federované služby.  
  
 [Postupy: vytvoření třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Popisuje postup konfigurace klientů a služeb, které používají `WSFederationHttpBinding`.  
  
 [Postupy: vytvoření služby tokenů zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Popisuje kroky k vytvoření služby tokenů zabezpečení.  
  
 [Zabezpečení Assertions Markup Language (SAML) tokenů a deklaracích identity](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Popisuje tokeny zabezpečení kontrolní výrazy Markup Language (SAML), které jsou rozšiřitelný a povolit vytvářet bohaté typy deklarací identity.  
  
 [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Popisuje postup vytvoření místního vystavitele tokenů zabezpečení.  
  
 [Postupy: zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Popisuje postup zakázání zabezpečených relací na `WSFederationHttpBinding`. Zakázání zabezpečených relací je nezbytné, při vytváření webové farmy, která vyžaduje relaci pro každého klienta.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Viz také  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Vlastní tokeny](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
