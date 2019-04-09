---
title: Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0ab343da821e8994ac3a652bfc55db261d5e48f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089481"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
Můžete certifikátů ve Windows Communication Foundation (WCF) se zabezpečením vrstvy zpráv (protokolu SOAP) kromě zabezpečení přenosové vrstvy (TLS) přes HTTP (HTTPS) nebo TCP. Toto téma popisuje rozdíly v způsob, jakým tyto certifikáty se ověřují.  
  
## <a name="validation-of-https-client-certificates"></a>Ověřování klientských certifikátů protokolu HTTPS  
 Při použití protokolu HTTPS pro komunikaci mezi klientem a službou, certifikát, který klient používá k ověření ve službě musí podporovat řetězce důvěryhodnosti. To znamená ho musí být propojeny s důvěryhodné kořenové certifikační autority. Pokud ne, vyvolá vrstvy protokolu HTTP <xref:System.Net.WebException> se zprávou "vzdálený server vrátil chybu: (403) zakázán." Vyvolá tuto výjimku jako WCF <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Ověření certifikátů služby protokolu HTTPS  
 Při použití protokolu HTTPS pro komunikaci mezi klientem a službou, certifikát, který se ověřuje na serveru musí podporovat řetězce důvěryhodnosti ve výchozím nastavení. To znamená ho musí být propojeny s důvěryhodné kořenové certifikační autority. Pokud chcete zobrazit, jestli certifikát byl odvolán je provedena žádná kontrola online. Toto chování můžete přepsat tak, že zaregistrujete <xref:System.Net.Security.RemoteCertificateValidationCallback> zpětné volání, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 kde podpis pro `ValidateServerCertificate` vypadá takto:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementace `ValidateServerCertificate` můžete provést žádné kontroly, které vývojář aplikace klienta považuje za nutné ověřit certifikát služby.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Ověřování klientských certifikátů SSL přes TCP a SOAP zabezpečení  
 Při použití vrstvy SSL (Secure Sockets) přes protokol TCP nebo zabezpečení zpráv (protokolu SOAP), klientské certifikáty se ověřují podle <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> hodnotu vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty. Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> hodnotu vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Ověřovací certifikát služby v SSL přes TCP a SOAP zabezpečení  
 Při použití protokolu SSL přes TCP a (SOAP) zabezpečení zpráv, služba certifikáty se ověřují podle <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> hodnotu vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty.  
  
 Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> hodnotu vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
