---
title: Běžné scénáře zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 578ec2d7d5abe1285007ad22d8bacd69e695b1d3
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964281"
---
# <a name="common-security-scenarios"></a>Běžné scénáře zabezpečení
Témata v tomto oddílu katalogují několik možných konfigurací zabezpečení klientů a služeb. Konfigurace se liší v závislosti na mnoha faktorech. Například zda je služba nebo klient v intranetu nebo zda je zabezpečení poskytované systémem Windows nebo přenos (například HTTPS).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezabezpečený internetový klient a služba](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Příklad veřejného nezabezpečeného klienta a služby.  
  
 [Nezabezpečený intranetový klient a služba](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Služba WCF (Basic Windows Communication Foundation) vyvinutá tak, aby poskytovala informace o zabezpečené privátní síti pro aplikaci WCF.  
  
 [Zabezpečení přenosu pomocí základního ověřování](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikace umožňuje klientům přihlašovat se pomocí vlastního ověřování.  
  
 [Zabezpečení přenosu pomocí ověřování Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Zobrazuje klienta a službu zabezpečený zabezpečením systému Windows.  
  
 [Zabezpečení přenosu pomocí anonymního klienta](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Tento scénář používá zabezpečení přenosu (například HTTPS) k zajištění důvěrnosti a integrity.  
  
 [Zabezpečení přenosu pomocí ověření certifikátem](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Zobrazuje klienta a službu zabezpečený certifikátem.  
  
 [Zabezpečení zpráv pomocí anonymního klienta](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Zobrazuje klienta a službu zabezpečený zabezpečením zpráv WCF.  
  
 [Zabezpečení zpráv pomocí klienta uživatelského jména](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient je model Windows Forms aplikace, která klientům umožňuje přihlásit se pomocí uživatelského jména a hesla domény.  
  
 [Zabezpečení zpráv pomocí klientských certifikátů](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Servery mají certifikáty a každý z klientů má certifikát. Kontext zabezpečení je vytvořen pomocí vyjednávání protokolu TLS (Transport Layer Security).  
  
 [Zabezpečení zprávy pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Variace klienta certifikátu. Servery mají certifikáty a každý z klientů má certifikát. Kontext zabezpečení je vytvořen prostřednictvím vyjednávání TLS.  
  
 [Zabezpečení zpráv pomocí klienta Windows bez vyjednávání přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Zobrazuje klienta a službu zabezpečenou doménou protokolu Kerberos.  
  
 [Zabezpečení zpráv pomocí vzájemných certifikátů](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Servery mají certifikáty a každý z klientů má certifikát. Certifikát serveru je distribuován s aplikací a je dostupný mimo IP síť.  
  
 [Zabezpečení zpráv pomocí vystavených tokenů](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Federované zabezpečení, které umožňuje vytvoření vztahu důvěryhodnosti mezi nezávislými doménami.  
  
 [Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient přistupuje k jedné nebo více webovým službám, které jsou distribuovány přes síť. Webové služby mají přístup k dalším prostředkům (jako jsou databáze nebo jiné webové služby), které musí být zabezpečené.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Informace o zabezpečení a osvědčené postupy](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
