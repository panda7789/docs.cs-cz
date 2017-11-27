---
title: "Možnosti zabezpečení u vlastních vazeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Možnosti zabezpečení u vlastních vazeb
Běžné úkoly, zabezpečení můžete provést pomocí jedné z vazby poskytované systémem. Pokud potřebujete větší kontrolu, ale můžete vytvořit vlastní vazby s <xref:System.ServiceModel.Channels.SecurityBindingElement>, jak je popsáno v těchto tématech. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vlastní vazby, najdete v části [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Popisuje režimy ověřování, které lze prostřednictvím vlastní vazby.  
  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Popisuje základní kroky pro vytvoření vlastní vazby s elementem zabezpečení.  
  
 [Postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Popisuje, jak vytvořit element zabezpečení pro zadaný režim ověřování.  
  
 [Postupy: zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Popisuje postup zakázání zabezpečených relací při vytváření služby federation service.  
  
 [Postupy: Povolení zjišťování opakování zpráv](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Popisuje, jak určit, kdy dojde k útoku formou opakovaného přehrávání.  
  
 [Postupy: vytvoření přihlašovacích údajů podpora](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Popisuje, jak zadat podpůrné pověření pro služby, pokud služba vyžaduje, aby ho.  
  
 [Postupy: nastavení potvrzení podpisu](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Popisuje postup při digitálnímu podepisování zpráv potvrďte podpisy.  
  
 [Postupy: Sada zkosení max. frekvence](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Popisuje, jak nastavit maximální povolený časový rozdíl mezi službou a klienta.  
  
 [Postupy: Zakázání šifrování digitálních podpisů](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Popisuje, jak zakázáním šifrování digitálních podpisů může mít výhody výkonu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Princip úrovně ochrany](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Viz také  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
