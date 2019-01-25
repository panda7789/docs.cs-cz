---
title: Federace a vystavené tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 513d68f49e4182979b492fa67e65860aee96e09a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699412"
---
# <a name="federation-and-issued-tokens"></a>Federace a vystavené tokeny
S Windows Communication Foundation (WCF), můžete vytvořit klienty, kteří zabezpečeně komunikují se službami, které implementují specifikace WS-Federation a WS-Trust. Specifikace poskytují mechanismy, které umožňují ověřování a autorizace ve sférách různých důvěryhodnosti pomocí XML a SOAP, webové služby WSDL (Description Language).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 Poskytuje přehled federace.  
  
 [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Uvádí problémy návrhu je potřeba vědět při vytváření federované služby nebo klientů.  
  
 [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Popisuje základní informace o vytvoření federovaného klienta s použitím technologie WCF.  
  
 [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Popisuje kroky k vytvoření federovaného služby.  
  
 [Postupy: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Popisuje postup konfigurace klientů a služeb, které používají `WSFederationHttpBinding`.  
  
 [Postupy: Vytvoření služby tokenů zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Popisuje kroky k vytvoření služby tokenů zabezpečení.  
  
 [Tokeny a deklarace identity jazyka SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Popisuje tokeny zabezpečení kontrolní výrazy SAML (Markup Language), které jsou rozšiřitelné a umožňují vytvářet bohaté typy deklarací identity.  
  
 [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Popisuje postup vytvoření lokálního vystavitele tokenů zabezpečení.  
  
 [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
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
  
## <a name="see-also"></a>Viz také:
- [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Vlastní tokeny](../../../../docs/framework/wcf/extending/custom-tokens.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
