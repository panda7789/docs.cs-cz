---
title: Běžné scénáře zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: af58d6b529fba32380bedb9a892a2b1fd4807d96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199268"
---
# <a name="common-security-scenarios"></a>Běžné scénáře zabezpečení
Témata v této části katalogu počet možných klienta a konfigurace zabezpečení služby. Konfigurace se liší podle počtu faktorů. Například, jestli je služba nebo klient na intranetu, nebo určuje, zda je zabezpečení poskytované Windows nebo přenosu (například HTTPS).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nezabezpečený internetový klient a služba](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Příkladem veřejného, zabezpečená klienta a služby.  
  
 [Nezabezpečený intranetový klient a služba](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Základní služby Windows Communication Foundation (WCF) vyvinuta poskytují informace o zabezpečené privátní sítě pro aplikace WCF.  
  
 [Zabezpečení přenosu pomocí základního ověřování](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikace umožňuje klientům přihlášení pomocí vlastní ověřování.  
  
 [Zabezpečení přenosu pomocí ověřování Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Ukazuje klienta a služby zabezpečuje zabezpečení Windows.  
  
 [Zabezpečení přenosu pomocí anonymního klienta](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Tento scénář využívá k zajištění důvěrnost a integrita zabezpečení přenosu (například HTTPS).  
  
 [Zabezpečení přenosu pomocí ověření certifikátem](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Ukazuje klienta a služby zabezpečené pomocí certifikátu.  
  
 [Zabezpečení zpráv pomocí anonymního klienta](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Ukazuje klienta a služby zabezpečuje zabezpečení zpráv WCF.  
  
 [Zabezpečení zpráv pomocí klienta uživatelského jména](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient je aplikace Windows Forms, která umožňuje klientům k přihlášení pomocí doménového uživatelského jména a hesla.  
  
 [Zabezpečení zpráv pomocí klientských certifikátů](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Servery mají certifikáty a každý klient má certifikát. Kontext zabezpečení se navazuje prostřednictvím vyjednávání zabezpečení TLS (Transport Layer).  
  
 [Zabezpečení zprávy pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Změna certifikátu klienta. Servery mají certifikáty a každý klient má certifikát. Kontext zabezpečení se navazuje prostřednictvím vyjednávání TLS.  
  
 [Zabezpečení zpráv pomocí klienta Windows bez vyjednávání přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Ukazuje klienta a služby zabezpečené pomocí protokolu Kerberos domény.  
  
 [Zabezpečení zpráv pomocí vzájemných certifikátů](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Servery mají certifikáty a každý klient má certifikát. Certifikát serveru je distribuován s aplikací a je k dispozici mimo pásmo.  
  
 [Zabezpečení zpráv pomocí vystavených tokenů](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Zabezpečení, která umožní navázání vztahu důvěryhodnosti mezi doménami nezávislé.  
  
 [Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient přistupuje k jedné nebo více webových služeb, které jsou distribuovány napříč sítí. Webové služby přístup k dalším prostředkům (jako jsou databáze nebo jiné webové služby), které musí být zabezpečená.  
  
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
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
