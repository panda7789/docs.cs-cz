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
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696441"
---
# <a name="custom-credential-and-credential-validation"></a>Vlastní pověření a ověřování pověření
Zabezpečení Windows Communication Foundation (WCF) je založeno na výměnou přihlašovacích údajů mezi služeb a klientů. Většina scénářů zabezpečení je možné splnit pomocí běžných typů přihlašovacích údajů, jako jsou Windows (Kerberos), uživatelského jména a hesla a certifikáty. Ale pokud se vyžaduje nový typ přihlašovacích údajů, témata v této části popisují, jak zpracovat a nové typy ověření.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Vysvětluje, jak přizpůsobit WCF ověření děděním z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
 [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Ukazuje, jak rozšířit <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy tak, aby vyhovovaly nových přihlašovacích údajů typy. Toto je první v řadě témat, které umožňují vytváření typů vlastních přihlašovacích údajů.  
  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení ke zpracování nových typů přihlašovacích údajů a vrátí nové tokeny pro přihlašovací údaje. Toto je druhá téma v řadě.  
  
 [Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Vysvětluje, jak vytvořit vlastní ověřovací data k ověření nový typ přihlašovacích údajů. Toto je třetí téma v řadě.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
