---
title: <clientCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673300"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="c445d-102">\<clientCertificate> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c445d-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="c445d-103">Určuje certifikát X.509 použitý k podepisování a šifrování zpráv do formuláře klienta služby v duplexním komunikačním režimu.</span><span class="sxs-lookup"><span data-stu-id="c445d-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="c445d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c445d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c445d-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c445d-105">\<behaviors></span></span>  
<span data-ttu-id="c445d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c445d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c445d-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c445d-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="c445d-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c445d-108">\<behavior></span></span>  
<span data-ttu-id="c445d-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c445d-109">\<serviceCredentials></span></span>  
<span data-ttu-id="c445d-110">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="c445d-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c445d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c445d-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c445d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c445d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c445d-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c445d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c445d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="c445d-114">Attributes</span></span>  
 <span data-ttu-id="c445d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c445d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c445d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c445d-116">Child Elements</span></span>  
  
|<span data-ttu-id="c445d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="c445d-117">Element</span></span>|<span data-ttu-id="c445d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c445d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c445d-119">\<authentication></span><span class="sxs-lookup"><span data-stu-id="c445d-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="c445d-120">Určuje možnosti ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c445d-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="c445d-121">\<certificate></span><span class="sxs-lookup"><span data-stu-id="c445d-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="c445d-122">Určuje certifikát, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c445d-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c445d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c445d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c445d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c445d-124">Element</span></span>|<span data-ttu-id="c445d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c445d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c445d-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c445d-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="c445d-127">Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="c445d-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c445d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c445d-128">Remarks</span></span>  
 <span data-ttu-id="c445d-129">Tento element se používá při služba musí mít certifikát klienta předem k bezpečné komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="c445d-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="c445d-130">Vyvolá se při použití vzoru duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="c445d-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="c445d-131">Ve vzoru obvyklejší žádostí a odpovědí klient zahrne svůj certifikát v požadavku, který službu používá k šifrování a podepisování odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="c445d-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="c445d-132">Ve vzoru duplexní komunikaci ale služba nemá žádosti z klienta a proto potřebuje certifikát klienta předem pro zabezpečené zprávy do klienta.</span><span class="sxs-lookup"><span data-stu-id="c445d-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="c445d-133">Proto musíte získat certifikát klienta v vyjednávání out-of-band a vyberte certifikát pro použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="c445d-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="c445d-134">Další informace o duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="c445d-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="c445d-135">Certifikát, nastavte v tomto elementu se používá k šifrování zpráv klienta jenom u vazeb, které jsou nakonfigurovány s `MutualCertificateDuplex` režim ověřování zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="c445d-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c445d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c445d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="c445d-137">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="c445d-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="c445d-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c445d-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c445d-139">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="c445d-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
