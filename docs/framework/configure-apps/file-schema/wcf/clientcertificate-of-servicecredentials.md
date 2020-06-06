---
title: <clientCertificate> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398141"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="bb928-102">\<clientCertificate> z \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bb928-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="bb928-103">Definuje certifikát X. 509, který se používá k podpisu a šifrování zpráv na straně klienta ve formě duplexního komunikačního vzoru.</span><span class="sxs-lookup"><span data-stu-id="bb928-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="bb928-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb928-104">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb928-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb928-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bb928-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb928-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb928-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb928-107">Attributes</span></span>  
 <span data-ttu-id="bb928-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="bb928-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb928-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb928-109">Child Elements</span></span>  
  
|<span data-ttu-id="bb928-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb928-110">Element</span></span>|<span data-ttu-id="bb928-111">Description</span><span class="sxs-lookup"><span data-stu-id="bb928-111">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="bb928-112">Určuje možnosti ověřování pro klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="bb928-112">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="bb928-113">Určuje certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="bb928-113">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb928-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb928-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bb928-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb928-115">Element</span></span>|<span data-ttu-id="bb928-116">Description</span><span class="sxs-lookup"><span data-stu-id="bb928-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="bb928-117">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřováním přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="bb928-117">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb928-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb928-118">Remarks</span></span>  
 <span data-ttu-id="bb928-119">Tento prvek se používá v případě, že služba musí mít certifikát klienta předem pro zabezpečenou komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="bb928-119">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="bb928-120">K tomu dochází při použití duplexního způsobu komunikace.</span><span class="sxs-lookup"><span data-stu-id="bb928-120">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="bb928-121">V typickém vzoru požadavků a odpovědí klient zahrne svůj certifikát do žádosti, kterou služba používá k šifrování a podepsání své odpovědi zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="bb928-121">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="bb928-122">Ve způsobu duplexního přenosu však služba nemá požadavek od klienta, a proto potřebuje certifikát klienta předem, aby bylo možné zprávu zabezpečit klientovi.</span><span class="sxs-lookup"><span data-stu-id="bb928-122">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="bb928-123">Proto je nutné získat certifikát klienta při vzdáleném vyjednávání a zadat certifikát pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="bb928-123">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="bb928-124">Další informace o duplexních službách najdete v tématu [Postupy: Vytvoření duplexního kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="bb928-124">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="bb928-125">Certifikát nastavený v tomto elementu se používá k šifrování zpráv klientovi jenom pro vazby, které jsou nakonfigurované s `MutualCertificateDuplex` režimem ověřování zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="bb928-125">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb928-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb928-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="bb928-127">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="bb928-127">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="bb928-128">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb928-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bb928-129">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="bb928-129">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
