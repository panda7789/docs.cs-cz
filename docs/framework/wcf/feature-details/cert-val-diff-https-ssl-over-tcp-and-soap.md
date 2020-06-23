---
title: Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
description: Přečtěte si o certifikátech se zabezpečením pomocí protokolu SOAP (Message-Layer), které WCF nabízí kromě protokolu HTTPS nebo TCP, a o tom, jak WCF tyto certifikáty ověřuje.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 97d51e5b65ebf20e80a69512370b68a51eeb28a7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245268"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
Kromě protokolu TLS (Transport Layer Security) přes protokol HTTP (HTTPS) nebo TCP můžete použít certifikáty ve službě Windows Communication Foundation (WCF) se zabezpečením protokolu SOAP (Message-Layer). Toto téma popisuje rozdíly v způsobu ověření certifikátů.  
  
## <a name="validation-of-https-client-certificates"></a>Ověřování klientských certifikátů HTTPS  
 Pokud ke komunikaci mezi klientem a službou používáte protokol HTTPS, musí certifikát, který klient používá k ověření služby, podporovat vztah důvěryhodnosti řetězu. To znamená, že musí být zřetězené s důvěryhodnou kořenovou certifikační autoritou. V takovém případě vrstva HTTP vyvolá <xref:System.Net.WebException> zprávu "vzdálený server vrátil chybu: (403) zakázáno." WCF vyvolá tuto výjimku jako <xref:System.ServiceModel.Security.MessageSecurityException> .  
  
## <a name="validation-of-https-service-certificates"></a>Ověření certifikátů služby HTTPS  
 Pokud ke komunikaci mezi klientem a službou používáte protokol HTTPS, musí certifikát, pomocí kterého se Server ověřuje, podporovat důvěryhodnost řetězu ve výchozím nastavení. To znamená, že musí být zřetězené s důvěryhodnou kořenovou certifikační autoritou. K zjištění, zda byl certifikát odvolán, se neprovede žádná online kontroly. Toto chování můžete přepsat registrací <xref:System.Net.Security.RemoteCertificateValidationCallback> zpětného volání, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 podpis pro `ValidateServerCertificate` je následující:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementace nástroje `ValidateServerCertificate` může provádět všechny kontroly, které vývojář klientské aplikace považuje za nutné k ověření certifikátu služby.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Ověření klientských certifikátů v zabezpečení SSL přes TCP nebo SOAP  
 Při použití protokolu SSL (SSL (Secure Sockets Layer)) přes zabezpečení protokolu TCP nebo zprávy (SOAP) jsou certifikáty klientů ověřovány podle <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> hodnoty vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnot. Kontrola odvolání se provádí podle hodnot hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnot.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Ověření certifikátu služby v SSL přes TCP a SOAP Security  
 Při použití zabezpečení protokolu SSL přes protokol TCP nebo (SOAP) se certifikáty služby ověřují podle <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> hodnoty vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnot.  
  
 Kontrola odvolání se provádí podle hodnot hodnoty <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Vlastnost je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnot.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Práce s certifikáty](working-with-certificates.md)
