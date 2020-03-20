---
title: Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0e82d1898bec7cda474a5a92958b5af1b30c9de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185411"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP
Certifikáty v systému Windows Communication Foundation (WCF) můžete používat se zabezpečením vrstvy zpráv (SOAP) kromě zabezpečení tls (transportní vrstvy) přes PROTOKOL HTTP (HTTPS) nebo TCP. Toto téma popisuje rozdíly ve způsobu ověřování těchto certifikátů.  
  
## <a name="validation-of-https-client-certificates"></a>Ověření klientských certifikátů HTTPS  
 Při použití protokolu HTTPS ke komunikaci mezi klientem a službou musí certifikát, který klient používá k ověření služby, podporovat důvěryhodnost řetězce. To znamená, že musí zřetězit důvěryhodnou kořenovou certifikační autoritu. Pokud tomu tak není, <xref:System.Net.WebException> vrstva HTTP vyvolá se zprávou "Vzdálený server vrátil chybu: (403) Zakázáno." WCF zobrazí tuto <xref:System.ServiceModel.Security.MessageSecurityException>výjimku jako .  
  
## <a name="validation-of-https-service-certificates"></a>Ověření certifikátů služby HTTPS  
 Při použití protokolu HTTPS ke komunikaci mezi klientem a službou musí certifikát, který server ověřuje, ve výchozím nastavení podporovat důvěryhodnost řetězce. To znamená, že musí zřetězit důvěryhodnou kořenovou certifikační autoritu. Není provedena žádná online kontrola, která by zjistila, zda byl certifikát odvolán. Toto chování můžete přepsat registrací zpětného <xref:System.Net.Security.RemoteCertificateValidationCallback> volání, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 pokud `ValidateServerCertificate` je podpis pro:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementace `ValidateServerCertificate` může provádět všechny kontroly, které vývojář klientské aplikace považuje za nezbytné k ověření certifikátu služby.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Ověření klientských certifikátů v protokolu SSL přes zabezpečení PROTOKOLU TCP nebo SOAP  
 Při použití ssl (Secure Sockets Layer) přes TCP nebo zabezpečení zprávy (SOAP) jsou klientské certifikáty ověřeny podle hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy. Vlastnost je nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode> jednu z hodnot. Kontrola odvolání se provádí podle hodnot <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> hodnoty hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> vlastnosti třídy. Vlastnost je nastavena na <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> jednu z hodnot.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Ověření certifikátu služby v protokolu SSL přes zabezpečení PROTOKOLU TCP a SOAP  
 Při použití protokolu SSL přes zabezpečení zpráv TCP nebo (SOAP) <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> jsou certifikáty služby ověřeny podle hodnoty vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy. Vlastnost je nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode> jednu z hodnot.  
  
 Kontrola odvolání se provádí podle hodnot <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> hodnoty hodnoty <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> vlastnosti třídy. Vlastnost je nastavena na <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> jednu z hodnot.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
