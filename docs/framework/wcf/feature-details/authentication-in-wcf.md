---
title: Ověřování ve WCF
description: Přečtěte si o několika mechanismech služby WCF, které poskytují ověřování, jako je ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a heslo.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 4c3348cfb84b8571dc1f24b774ffcd691aaa5001
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247517"
---
# <a name="authentication-in-wcf"></a>Ověřování ve WCF
V následujících tématech najdete řadu různých mechanismů v Windows Communication Foundation (WCF), které poskytují ověřování, například ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a hesla.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Používání poskytovatele členství ASP.NET](how-to-use-the-aspnet-membership-provider.md)  
 Funkce ASP.NET zahrnují členství a poskytovatele rolí, databázi pro ukládání párů uživatelských jmen a hesel pro ověřování a role uživatelů pro autorizaci. Toto téma vysvětluje, jak můžou služby WCF používat stejnou databázi k ověřování a autorizaci uživatelů.  
  
 [Postupy: Použití validátoru vlastního uživatelského jména a hesla](how-to-use-a-custom-user-name-and-password-validator.md)  
 Ukazuje, jak integrovat vlastní validátor uživatelského jména a hesla.  
  
 [Identita a ověřování služby](service-identity-and-authentication.md)  
 Jako dodatečná ochrana může klient ověřit službu zadáním očekávané *identity* služby. Pokud Očekávaná identita a identita, kterou služba vrátila, se neshodují, ověřování se nezdařilo.  
  
 [Vyjednávání a časové limity zabezpečení](security-negotiation-and-timeouts.md)  
 Popisuje, jak použít <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídě.  
  
 [Ladění chyb u ověřování Windows](debugging-windows-authentication-errors.md)  
 Při použití ověřování systému Windows se zaměřuje na běžné problémy, ke kterým došlo.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Související oddíly  
 [Běžné scénáře zabezpečení](common-security-scenarios.md)  
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
