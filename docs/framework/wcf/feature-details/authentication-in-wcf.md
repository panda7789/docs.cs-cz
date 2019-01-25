---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 22bfd7edf0ca0e9eb57e63c168c783f25782d607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523919"
---
# <a name="authentication-in-wcf"></a>Ověřování ve WCF
Následující témata ukazují celou řadou různých mechanismů ve Windows Communication Foundation (WCF), které poskytují ověřování, například, ověřování Windows, certifikáty X.509 a uživatelského jména a hesla.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 Funkce ASP.NET zahrnují členství a zprostředkovatel rolí, databázi k ukládání párů jméno/heslo uživatele pro ověřování a uživatelských rolí pro autorizaci. Toto téma vysvětluje, jak můžete používat stejnou databázi k ověřování a autorizaci uživatelů služby WCF.  
  
 [Postupy: Pomocí vlastního uživatelského jména a hesla program pro ověření](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Ukazuje, jak integrovat validátor vlastní uživatelské jméno/heslo.  
  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Jako dodatečné zabezpečení, klient může ověřit službu tak, že zadáte očekávané *identity* služby. Pokud je Očekávaná identita neshodují identity vrácené službou, ověření se nezdaří.  
  
 [Vyjednávání a časové limity zabezpečení](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 Popisuje způsob použití <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy.  
  
 [Ladění chyb u ověřování Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Zaměřuje se na běžné problémy při použití ověřování Windows.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Související oddíly  
 [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Viz také:
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
