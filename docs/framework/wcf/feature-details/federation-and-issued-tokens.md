---
title: Federace a vystavené tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: d566388279f9210f70ebdb5c42512aea0425a47e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964596"
---
# <a name="federation-and-issued-tokens"></a>Federace a vystavené tokeny
Pomocí Windows Communication Foundation (WCF) můžete vytvořit klienty, kteří budou zabezpečeně komunikovat se službami, které implementují specifikace WS-Federation a WS-Trust. Specifikace používají XML, SOAP a Web Services Description Language (WSDL) k poskytování mechanismů, které umožňují ověřování a autorizaci napříč různými sférami vztahu důvěryhodnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 Poskytuje přehled federace.  
  
 [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Uvádí aspekty návrhu, které je potřeba znát při vytváření federovaných služeb nebo klientů.  
  
 [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Popisuje základy vytvoření federovaného klienta pomocí WCF.  
  
 [Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Popisuje kroky při vytváření federované služby.  
  
 [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 V této části najdete popis postupu konfigurace klientů a služeb, které používají `WSFederationHttpBinding`.  
  
 [Postupy: Vytvoření služby tokenů zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Popisuje kroky pro vytvoření služby tokenu zabezpečení.  
  
 [Tokeny a deklarace identity jazyka SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Popisuje tokeny SAML (Security Assert Markup Language), které jsou rozšiřitelné a umožňují vytvářet bohatý typy deklarací identity.  
  
 [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 V této části najdete popis postupu vytvoření místního vystavitele tokenů zabezpečení.  
  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Popisuje, jak zakázat zabezpečené relace na `WSFederationHttpBinding`. Při vytváření webové farmy, která vyžaduje relaci pro každého klienta, je nutné zakázat zabezpečené relace.  
  
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
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
