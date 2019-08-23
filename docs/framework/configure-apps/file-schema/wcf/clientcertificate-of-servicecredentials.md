---
title: <clientCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 277e5e33bcc7f9d417da7ce24caa4c6200c23e23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919540"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="91570-102">\<ClientCertificate > \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="91570-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="91570-103">Definuje certifikát X. 509, který se používá k podpisu a šifrování zpráv na straně klienta ve formě duplexního komunikačního vzoru.</span><span class="sxs-lookup"><span data-stu-id="91570-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="91570-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="91570-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="91570-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="91570-105">\<behaviors></span></span>  
<span data-ttu-id="91570-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="91570-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="91570-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="91570-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="91570-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="91570-108">\<behavior></span></span>  
<span data-ttu-id="91570-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="91570-109">\<serviceCredentials></span></span>  
<span data-ttu-id="91570-110">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="91570-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91570-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91570-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91570-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="91570-112">Attributes and Elements</span></span>  
 <span data-ttu-id="91570-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="91570-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91570-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="91570-114">Attributes</span></span>  
 <span data-ttu-id="91570-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="91570-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91570-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="91570-116">Child Elements</span></span>  
  
|<span data-ttu-id="91570-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="91570-117">Element</span></span>|<span data-ttu-id="91570-118">Popis</span><span class="sxs-lookup"><span data-stu-id="91570-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91570-119">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="91570-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="91570-120">Určuje možnosti ověřování pro klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="91570-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="91570-121">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="91570-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="91570-122">Určuje certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="91570-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91570-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="91570-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91570-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="91570-124">Element</span></span>|<span data-ttu-id="91570-125">Popis</span><span class="sxs-lookup"><span data-stu-id="91570-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91570-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="91570-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="91570-127">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="91570-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91570-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91570-128">Remarks</span></span>  
 <span data-ttu-id="91570-129">Tento prvek se používá v případě, že služba musí mít certifikát klienta předem pro zabezpečenou komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="91570-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="91570-130">K tomu dochází při použití duplexního způsobu komunikace.</span><span class="sxs-lookup"><span data-stu-id="91570-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="91570-131">V typickém vzoru požadavků a odpovědí klient zahrne svůj certifikát do žádosti, kterou služba používá k šifrování a podepsání své odpovědi zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="91570-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="91570-132">Ve způsobu duplexního přenosu však služba nemá požadavek od klienta, a proto potřebuje certifikát klienta předem, aby bylo možné zprávu zabezpečit klientovi.</span><span class="sxs-lookup"><span data-stu-id="91570-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="91570-133">Proto je nutné získat certifikát klienta při vzdáleném vyjednávání a zadat certifikát pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="91570-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="91570-134">Další informace o duplexních službách najdete v [tématu How to: Vytvoří oboustranný kontrakt](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="91570-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="91570-135">Certifikát nastavený v tomto elementu se používá k šifrování zpráv klientovi jenom pro vazby, které jsou nakonfigurované s `MutualCertificateDuplex` režimem ověřování zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="91570-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91570-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91570-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="91570-137">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="91570-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="91570-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="91570-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="91570-139">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="91570-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
