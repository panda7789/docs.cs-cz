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
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795816"
---
# <a name="custom-credential-and-credential-validation"></a>Vlastní pověření a ověřování pověření
Zabezpečení v Windows Communication Foundation (WCF) je založené na výměně přihlašovacích údajů mezi službami a klienty. Většinu scénářů zabezpečení je možné vyhovět pomocí běžných typů přihlašovacích údajů, jako je Windows (Kerberos), uživatelské jméno a hesla a certifikáty. Pokud je však požadován nový typ přihlašovacích údajů, témata v této části vysvětlují, jak zpracovávat a ověřovat nové typy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření služby, která používá vlastní validátor certifikátů](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Vysvětluje, jak přizpůsobit ověřování WCF děděním z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
 [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)  
 Ukazuje, jak rozšiřuje <xref:System.ServiceModel.Description.ClientCredentials> třídy a <xref:System.ServiceModel.Description.ServiceCredentials> pro přizpůsobení nových typů přihlašovacích údajů. Toto je první v řadě témat, která umožňují vytváření vlastních typů přihlašovacích údajů.  
  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)  
 Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení, který bude zpracovávat nové typy přihlašovacích údajů a vracet nové tokeny pro přihlašovací údaje. Toto je druhé téma v řadě.  
  
 [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)  
 Vysvětluje, jak vytvořit vlastní ověřovací data pro ověření nového typu přihlašovacích údajů. Toto je třetí téma v řadě.  
  
## <a name="reference"></a>Reference  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování](../feature-details/authentication-in-wcf.md)  
  
 [Federace a vystavené tokeny](../feature-details/federation-and-issued-tokens.md)  
  
 [Autorizace](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../feature-details/security.md)
