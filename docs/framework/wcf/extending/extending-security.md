---
title: Rozšíření zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797129"
---
# <a name="extending-security"></a>Rozšíření zabezpečení
Chcete-li přizpůsobit nové typy deklarací identity a vlastní tokeny, můžete roztáhnout infrastrukturu zabezpečení Windows Communication Foundation (WCF). Témata v této části vám ukážou, jak to uděláte.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
 [Vlastní přihlašovací údaje a jejich ověřování](custom-credential-and-credential-validation.md)  
 Vysvětluje, jak se používá model identity při ověřování vlastních přihlašovacích údajů.  
  
 [Vlastní tokeny](custom-tokens.md)  
 Vydané tokeny ze služby tokenů zabezpečení (STS) jsou obvykle tokeny SAML. Toto téma vysvětluje, jak vytvořit vlastní typ tokenu.  
  
 [Vlastní autorizace](custom-authorization.md)  
 Vysvětluje, jak implementovat vlastní autorizaci.  
  
 [Přepsání identity služby kvůli ověřování](overriding-the-identity-of-a-service-for-authentication.md)  
 Popisuje, jak přepsat identitu služby pro ověřování.  
  
 [Postupy: Vytvoření vlastního ověřovatele identity klienta](how-to-create-a-custom-client-identity-verifier.md)  
 Ukazuje, jak ověřit identitu vlastního koncového bodu.  
  
 [Postupy: Použití samostatných certifikátů X. 509 pro podepisování a šifrování](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Zprávy jsou obvykle podepsané a šifrované pomocí jednoho certifikátu. V tomto tématu se dozvíte, jak můžou být v případě potřeby použity dva certifikáty.  
  
 [Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X. 509](change-cryptographic-provider-x509-certificate-private-key.md)  
 Vysvětluje, jak změnit zprostředkovatele kryptografických služeb, který poskytuje privátní klíč certifikátu X. 509 a jak integrovat zprostředkovatele do architektury Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Reference  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Související oddíly  
 [Zabezpečení](../feature-details/security.md)  
  
 [Základní programování WCF](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../feature-details/security-overview.md)
