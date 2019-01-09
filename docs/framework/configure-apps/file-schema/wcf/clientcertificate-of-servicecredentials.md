---
title: '&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 7f777fd0e09a1bb9491f346a8e9806627aa63441
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145494"
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="dc9f9-102">&lt;clientCertificate&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="dc9f9-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="dc9f9-103">Určuje certifikát X.509 použitý k podepisování a šifrování zpráv do formuláře klienta služby v duplexním komunikačním režimu.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="dc9f9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dc9f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc9f9-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-105">\<behaviors></span></span>  
<span data-ttu-id="dc9f9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="dc9f9-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="dc9f9-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-108">\<behavior></span></span>  
<span data-ttu-id="dc9f9-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-109">\<serviceCredentials></span></span>  
<span data-ttu-id="dc9f9-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9f9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc9f9-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc9f9-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc9f9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc9f9-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc9f9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc9f9-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc9f9-114">Attributes</span></span>  
 <span data-ttu-id="dc9f9-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="dc9f9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc9f9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc9f9-116">Child Elements</span></span>  
  
|<span data-ttu-id="dc9f9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc9f9-117">Element</span></span>|<span data-ttu-id="dc9f9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="dc9f9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc9f9-119">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="dc9f9-120">Určuje možnosti ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="dc9f9-121">\<certifikát ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="dc9f9-122">Určuje certifikát, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc9f9-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc9f9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dc9f9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc9f9-124">Element</span></span>|<span data-ttu-id="dc9f9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="dc9f9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc9f9-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="dc9f9-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="dc9f9-127">Určuje přihlašovací údaje, který se má použít při ověřování služby, a nastavení příslušného ověřování přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc9f9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc9f9-128">Remarks</span></span>  
 <span data-ttu-id="dc9f9-129">Tento element se používá při služba musí mít certifikát klienta předem k bezpečné komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="dc9f9-130">Vyvolá se při použití vzoru duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="dc9f9-131">Ve vzoru obvyklejší žádostí a odpovědí klient zahrne svůj certifikát v požadavku, který službu používá k šifrování a podepisování odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="dc9f9-132">Ve vzoru duplexní komunikaci ale služba nemá žádosti z klienta a proto potřebuje certifikát klienta předem pro zabezpečené zprávy do klienta.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="dc9f9-133">Proto musíte získat certifikát klienta v vyjednávání out-of-band a vyberte certifikát pro použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="dc9f9-134">Další informace o duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dc9f9-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="dc9f9-135">Certifikát, nastavte v tomto elementu se používá k šifrování zpráv klienta jenom u vazeb, které jsou nakonfigurovány s `MutualCertificateDuplex` režim ověřování zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="dc9f9-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9f9-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc9f9-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="dc9f9-137">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="dc9f9-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="dc9f9-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dc9f9-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="dc9f9-139">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="dc9f9-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
