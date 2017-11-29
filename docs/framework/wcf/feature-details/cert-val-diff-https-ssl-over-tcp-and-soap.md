---
title: "Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b0a29b59b6b2f7b8dd3a430b2395b18c1e4f83fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="bfdaf-102">Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP</span><span class="sxs-lookup"><span data-stu-id="bfdaf-102">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>
<span data-ttu-id="bfdaf-103">Můžete použít certifikáty v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] s zabezpečení zpráv vrstvy (SOAP) kromě zabezpečení přenosové vrstvy (TLS) přes protokol HTTP (HTTPS) nebo TCP.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-103">You can use certificates in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="bfdaf-104">Toto téma popisuje rozdíly ve způsobu, jak tyto certifikáty se ověřují.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-104">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="bfdaf-105">Ověřování HTTPS klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="bfdaf-105">Validation of HTTPS Client Certificates</span></span>  
 <span data-ttu-id="bfdaf-106">Při použití protokolu HTTPS pro komunikaci mezi klientem a služby, certifikát, který klient používá k ověření služby musí podporovat řetězu vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-106">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="bfdaf-107">To znamená musí zřetězené důvěryhodné kořenové certifikační autoritě.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-107">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="bfdaf-108">Pokud ne, vyvolá vrstvě protokolu HTTP <xref:System.Net.WebException> se zprávou "vzdálený server vrátil chybu: (403) zakázán."</span><span class="sxs-lookup"><span data-stu-id="bfdaf-108">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bfdaf-109">vyvolá výjimku jako <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-109"> surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="bfdaf-110">Ověřování HTTPS služby certifikátů</span><span class="sxs-lookup"><span data-stu-id="bfdaf-110">Validation of HTTPS Service Certificates</span></span>  
 <span data-ttu-id="bfdaf-111">Při použití protokolu HTTPS pro komunikaci mezi klientem a služby, certifikát, který se ověřuje serveru musí podporovat řetěz důvěryhodnosti ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-111">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="bfdaf-112">To znamená musí zřetězené důvěryhodné kořenové certifikační autoritě.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-112">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="bfdaf-113">Pokud chcete zobrazit, zda certifikát byl odvolán je provedena žádná kontrola online.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-113">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="bfdaf-114">Toto chování můžete přepsat pomocí registrace <xref:System.Net.Security.RemoteCertificateValidationCallback> zpětné volání, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-114">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="bfdaf-115">kde podpis pro `ValidateServerCertificate` vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bfdaf-115">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="bfdaf-116">Implementace `ValidateServerCertificate` můžete provádět žádné kontroly, které vývojář aplikace klienta považuje za nezbytné k ověření certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-116">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="bfdaf-117">Ověřování klientských certifikátů v SSL přes TCP nebo zabezpečení protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="bfdaf-117">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  
 <span data-ttu-id="bfdaf-118">Když pomocí Secure Sockets Layer (SSL) přes TCP nebo zabezpečení zpráv (SOAP), klientské certifikáty se ověřují podle <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-118">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="bfdaf-119">Je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-119">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="bfdaf-120">Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-120">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="bfdaf-121">Je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-121">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="bfdaf-122">Ověření certifikátu služby, SSL přes TCP a SOAP zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bfdaf-122">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  
 <span data-ttu-id="bfdaf-123">Při použití protokolu SSL přes TCP nebo (SOAP) zabezpečení zpráv certifikáty služby se ověřují podle <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-123">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="bfdaf-124">Je nastavena na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-124">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="bfdaf-125">Kontrola odvolání se provádí podle hodnoty <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> hodnota vlastnosti <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-125">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="bfdaf-126">Je nastavena na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfdaf-126">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bfdaf-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfdaf-127">See Also</span></span>  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [<span data-ttu-id="bfdaf-128">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="bfdaf-128">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
