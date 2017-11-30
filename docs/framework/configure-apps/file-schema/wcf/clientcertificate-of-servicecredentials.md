---
title: "&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc4b3251a85a6926c93f418c154b4eabbd44092f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="f297e-102">&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="f297e-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="f297e-103">Definuje certifikátu X.509. certifikát použít k podepisování a šifrování zpráv do formuláře jako klienta služby ve tvaru duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="f297e-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="f297e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f297e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f297e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f297e-105">\<behaviors></span></span>  
<span data-ttu-id="f297e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f297e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f297e-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f297e-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="f297e-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f297e-108">\<behavior></span></span>  
<span data-ttu-id="f297e-109">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f297e-109">\<serviceCredentials></span></span>  
<span data-ttu-id="f297e-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f297e-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f297e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f297e-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f297e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f297e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f297e-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f297e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f297e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f297e-114">Attributes</span></span>  
 <span data-ttu-id="f297e-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="f297e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f297e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f297e-116">Child Elements</span></span>  
  
|<span data-ttu-id="f297e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f297e-117">Element</span></span>|<span data-ttu-id="f297e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f297e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f297e-119">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="f297e-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="f297e-120">Určuje možnosti ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="f297e-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="f297e-121">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="f297e-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="f297e-122">Určuje certifikát, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="f297e-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f297e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f297e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f297e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f297e-124">Element</span></span>|<span data-ttu-id="f297e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f297e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f297e-126">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f297e-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f297e-127">Určuje pověření, která mají být použity v ověřování služby, a ověření přihlašovacích údajů klienta související nastavení.</span><span class="sxs-lookup"><span data-stu-id="f297e-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f297e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f297e-128">Remarks</span></span>  
 <span data-ttu-id="f297e-129">Tento element se používá, pokud služba musí mít certifikát klienta předem pro bezpečnou komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="f297e-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="f297e-130">K tomu dochází, když pomocí vzoru duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="f297e-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="f297e-131">Ve vzoru typičtější požadavků a odpovědí klienta zahrnuje svůj certifikát v žádosti, které služba používá k šifrování a podepisování odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="f297e-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="f297e-132">Ve vzoru duplexní komunikace ale služba nemá požadavek od klienta a proto potřebuje certifikát klienta předem k zabezpečení zprávy do klienta.</span><span class="sxs-lookup"><span data-stu-id="f297e-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="f297e-133">Proto musíte získat certifikát klienta v vyjednávání out-of-band a zadat certifikát pomocí tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="f297e-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="f297e-134">Další informace o duplexní služby najdete v tématu [postupy: vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f297e-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="f297e-135">Nastavit v tomto elementu certifikát se používá k šifrování zpráv, které mají klienta jenom u vazeb, které jsou nakonfigurovány s `MutualCertificateDuplex` režim ověření zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f297e-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f297e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f297e-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="f297e-137">Postupy: vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="f297e-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="f297e-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f297e-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f297e-139">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f297e-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
