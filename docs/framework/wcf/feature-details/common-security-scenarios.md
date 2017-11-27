---
title: "Běžné scénáře zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9428c5d7c8c6cf0f571b05a8b9c33b96d073d7a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="common-security-scenarios"></a>Běžné scénáře zabezpečení
Témata v této části katalogu počet možných klienta a konfigurace zabezpečení služby. Konfigurace se liší podle počtu faktorů. Například jestli je služba nebo klienta na intranetu, nebo jestli poskytuje zabezpečení systému Windows nebo přenos (například HTTPS).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezabezpečený internetový klient a služba](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Příklad veřejné zabezpečená klienta a služby.  
  
 [Nezabezpečený intranetový klient a služba](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Základní [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby vyvinuté tak, aby poskytují informace o do zabezpečené privátní sítě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
 [Zabezpečení přenosu se základním ověřováním](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikace umožňuje klientům připojení pomocí vlastního ověřování.  
  
 [Zabezpečení přenosu pomocí ověřování systému Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Zobrazuje klienta a služby Zabezpečené zabezpečení systému Windows.  
  
 [Zabezpečení přenosu s anonymním klientem](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Tento scénář používá k zajištění důvěrnosti a integrity zabezpečení přenosu (například HTTPS).  
  
 [Zabezpečení přenosu s ověřováním pomocí certifikátu](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Zobrazuje klienta a služby Zabezpečené certifikát.  
  
 [Zabezpečení zpráv s anonymním klientem](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Ukazuje klienta a služby zabezpečené [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení zpráv.  
  
 [Zabezpečení zpráv s klientem uživatelského jména](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient je aplikace Windows Forms, která umožňuje klientům připojení pomocí domény uživatelské jméno a heslo.  
  
 [Zabezpečení zpráv pomocí klientských certifikátů](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Servery mají certifikáty a má každý klient certifikát. Kontext zabezpečení je vytvořeno prostřednictvím vyjednávání zabezpečení TLS (Transport Layer).  
  
 [Zabezpečení zpráv s klientem Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Varianta certifikát klienta. Servery mají certifikáty a má každý klient certifikát. Kontext zabezpečení je vytvořeno prostřednictvím vyjednávání TLS.  
  
 [Zabezpečení zpráv s klientem Windows bez vyjednávání pověření](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Zobrazuje klienta a služby zabezpečené pomocí protokolu Kerberos domény.  
  
 [Zabezpečení zpráv vzájemnými certifikáty](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Servery mají certifikáty a má každý klient certifikát. Certifikát serveru je distribuován s aplikací a je k dispozici vzdálené správy.  
  
 [Zabezpečení zpráv pomocí vydaných tokenů](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Federované zabezpečení, které umožní navázání vztahu důvěryhodnosti mezi doménami nezávislé.  
  
 [Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient přistupuje k jedné nebo více webových služeb, které jsou rozmístěny v síti. Webové služby k další prostředky (například databáze nebo jiných webových služeb), které musí být zabezpečená.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Související oddíly  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Viz také  
 [Informace o zabezpečení a doporučené postupy](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
