---
title: Rozšíření zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a16416e580dabd6a9057e11a8183437529ca83e8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560557"
---
# <a name="extending-security"></a>Rozšíření zabezpečení
Tak, aby vyhovovaly nové typy deklarací identity a vlastní tokeny, můžete rozšířit Infrastruktura zabezpečení Windows Communication Foundation (WCF). Témata v této části ukazují, jak to lze provést.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Architektura zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Provede architekturu jako systém zabezpečení WCF.  
  
 [Vlastní přihlašovací údaje a jejich ověřování](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Vysvětluje, jak modelem Identity se používá při ověřování vlastní přihlašovací údaje.  
  
 [Vlastní tokeny](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Vystavené tokeny z tokenu služby zabezpečení (STS) jsou obvykle tokeny SAML. Toto téma vysvětluje, jak vytvořit vlastní typ tokenu.  
  
 [Vlastní autorizace](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Vysvětluje, jak implementovat vlastní autorizace.  
  
 [Přepsání identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Popisuje přepsání identity služby kvůli ověřování.  
  
 [Postupy: Vytvoření vlastního ověřovatele identity klientů](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Ukazuje, jak se ověřit identitu vlastní koncový bod.  
  
 [Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Zprávy jsou obvykle podepsaný a zašifrovaný s jedním certifikátem. Toto téma vysvětluje, jak dva certifikáty je možné, v případě potřeby.  
  
 [Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Vysvětluje, jak změnit zprostředkovatele kryptografických služeb používají k zajištění privátní klíč certifikátu X.509 a jak integrovat zprostředkovatele do rozhraní Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Související oddíly  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
