---
title: Možnosti zabezpečení u vlastních vazeb
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595190"
---
# <a name="security-capabilities-with-custom-bindings"></a>Možnosti zabezpečení u vlastních vazeb
Většinu běžných úloh zabezpečení můžete provádět pomocí jedné z vazeb poskytovaných systémem. Pokud však potřebujete větší kontrolu, můžete vytvořit vlastní vazbu s a <xref:System.ServiceModel.Channels.SecurityBindingElement> , jak je vysvětleno v těchto tématech. Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md)  
 Popisuje režimy ověřování, které lze použít s vlastní vazbou.  
  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Popisuje základní kroky pro vytvoření vlastní vazby s prvkem zabezpečení.  
  
 [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Popisuje, jak vytvořit prvek zabezpečení pro zadaný režim ověřování.  
  
 [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Popisuje, jak zakázat zabezpečené relace při vytváření federační služby.  
  
 [Postupy: Povolení zjišťování opakování zpráv](how-to-enable-message-replay-detection.md)  
 Popisuje, jak určit, kdy dojde k útoku na opakování.  
  
 [Postupy: Vytvoření podpůrných přihlašovacích údajů](how-to-create-a-supporting-credential.md)  
 V této části najdete popis postupu poskytnutí podpůrného pověření ke službě, pokud je služba vyžaduje.  
  
 [Postupy: Nastavení potvrzení podpisu](how-to-set-up-a-signature-confirmation.md)  
 Popisuje kroky pro potvrzení podpisů při digitálním podepisování zprávy.  
  
 [Postupy: Nastavení hodnoty vlastnosti MaxClockSkew](how-to-set-a-max-clock-skew.md)  
 V této části najdete popis postupu nastavení maximálního povoleného časového rozdílu mezi službou a klientem.  
  
 [Postupy: Zákaz šifrování digitálních podpisů](how-to-disable-encryption-of-digital-signatures.md)  
 Popisuje, jak zakázat šifrování digitálních podpisů může mít výhody výkonu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Princip úrovně ochrany](../understanding-protection-level.md)  
  
 [Zabezpečení služeb a klientů](securing-services-and-clients.md)  
  
## <a name="see-also"></a>Viz také

- [Vazby a zabezpečení](bindings-and-security.md)
- [Přehled zabezpečení](security-overview.md)
- [Vazby poskytované systémem](../system-provided-bindings.md)
