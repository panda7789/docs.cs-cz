---
title: Vlastní pověření a ověřování pověření
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 9b340c01a9eb4ce4007e93f2b38e292cd6543ba1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803450"
---
# <a name="custom-credential-and-credential-validation"></a>Vlastní pověření a ověřování pověření
Zabezpečení ve Windows Communication Foundation (WCF) je založena na výměnu přihlašovacích údajů mezi služeb a klientů. Většina scénářů zabezpečení může obsloužit pomocí běžné typy přihlašovacích údajů, jako jsou Windows (Kerberos), uživatelského jména a hesla a certifikáty. Ale pokud nový typ pověření je zapotřebí, témata v této části popisují, jak ke zpracování a ověření nové typy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Vysvětluje, jak přizpůsobit WCF ověření, která dědí z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Ukazuje, jak rozšířit <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy pro uložení nové přihlašovací údaje typy. Toto je první v řadě témata, které umožňují vytváření typů vlastní pověření.  
  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení ke zpracování nových typů přihlašovacích údajů a vrátí nové tokeny pro přihlašovací údaje. Toto je druhý téma v řadě.  
  
 [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Vysvětluje, jak vytvořit vlastní ověřovací k ověření nový typ přihlašovacích údajů. Toto je třetí téma v řadě.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
