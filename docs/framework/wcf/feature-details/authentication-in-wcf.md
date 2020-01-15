---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964697"
---
# <a name="authentication-in-wcf"></a>Ověřování ve WCF
V následujících tématech najdete řadu různých mechanismů v Windows Communication Foundation (WCF), které poskytují ověřování, například ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a hesla.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 Funkce ASP.NET zahrnují členství a poskytovatele rolí, databázi pro ukládání párů uživatelských jmen a hesel pro ověřování a role uživatelů pro autorizaci. Toto téma vysvětluje, jak můžou služby WCF používat stejnou databázi k ověřování a autorizaci uživatelů.  
  
 [Postupy: Použití validátoru vlastního uživatelského jména a hesla](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Ukazuje, jak integrovat vlastní validátor uživatelského jména a hesla.  
  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Jako dodatečná ochrana může klient ověřit službu zadáním očekávané *identity* služby. Pokud Očekávaná identita a identita, kterou služba vrátila, se neshodují, ověřování se nezdařilo.  
  
 [Vyjednávání a časové limity zabezpečení](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 Popisuje, jak použít vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> ve třídě <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.  
  
 [Ladění chyb u ověřování Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Při použití ověřování systému Windows se zaměřuje na běžné problémy, ke kterým došlo.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Související oddíly  
 [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
