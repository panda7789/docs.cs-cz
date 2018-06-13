---
title: Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 744d9208f6be47965b89ddd9555b99feab9e18b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489466"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
Můžete použít certifikáty ve Windows Communication Foundation (WCF) s zabezpečení zpráv vrstvy (SOAP) kromě zabezpečení přenosové vrstvy (TLS) přes protokol HTTP (HTTPS) nebo TCP. Toto téma popisuje rozdíly ve způsobu, jak tyto certifikáty se ověřují.  
  
## <a name="validation-of-https-client-certificates"></a>Ověřování HTTPS klientských certifikátů  
 Při použití protokolu HTTPS pro komunikaci mezi klientem a služby, certifikát, který klient používá k ověření služby musí podporovat řetězu vztah důvěryhodnosti. To znamená musí zřetězené důvěryhodné kořenové certifikační autoritě. Pokud ne, vyvolá vrstvě protokolu HTTP <xref:System.Net.WebException> se zprávou "vzdálený server vrátil chybu: (403) zakázán." Vyvolá výjimku jako WCF <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Ověřování HTTPS služby certifikátů  
 Při použití protokolu HTTPS pro komunikaci mezi klientem a služby, certifikát, který se ověřuje serveru musí podporovat řetěz důvěryhodnosti ve výchozím nastavení. To znamená musí zřetězené důvěryhodné kořenové certifikační autoritě. Pokud chcete zobrazit, zda certifikát byl odvolán je provedena žádná kontrola online. Toto chování můžete přepsat pomocí registrace <xref:System.Net.Security.RemoteCertificateValidationCallback> zpětné volání, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 kde podpis pro `ValidateServerCertificate` vypadá takto:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementace `ValidateServerCertificate` můžete provádět žádné kontroly, které vývojář aplikace klienta považuje za nezbytné k ověření certifikátu služby.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Ověřování klientských certifikátů v SSL přes TCP nebo zabezpečení protokolu SOAP  
 Když pomocí Secure Sockets Layer (SSL) přes TCP nebo zabezpečení zpráv (SOAP), klientské certifikáty se ověřují podle <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty. Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Ověření certifikátu služby, SSL přes TCP a SOAP zabezpečení  
 Při použití protokolu SSL přes TCP nebo (SOAP) zabezpečení zpráv certifikáty služby se ověřují podle <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty.  
  
 Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
