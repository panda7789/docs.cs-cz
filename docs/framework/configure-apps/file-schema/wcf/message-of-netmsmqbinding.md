---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 060c7dc07e53d0114241ac7528a24363e78715c6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257174"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="3ad71-102">\<Zpráva > z \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="3ad71-102">\<message> of \<netMsmqBinding></span></span>
<span data-ttu-id="3ad71-103">Definuje nastavení založená na protokolu SOAP zprávy zabezpečení v tomto `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="3ad71-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="3ad71-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ad71-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ad71-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3ad71-105">\<bindings></span></span>  
<span data-ttu-id="3ad71-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="3ad71-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="3ad71-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ad71-107">\<binding></span></span>  
<span data-ttu-id="3ad71-108">\<security></span><span class="sxs-lookup"><span data-stu-id="3ad71-108">\<security></span></span>  
<span data-ttu-id="3ad71-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="3ad71-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad71-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ad71-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ad71-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ad71-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3ad71-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ad71-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ad71-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ad71-113">Attributes</span></span>  
  
|<span data-ttu-id="3ad71-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ad71-114">Attribute</span></span>|<span data-ttu-id="3ad71-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3ad71-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ad71-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3ad71-116">algorithmSuite</span></span>|<span data-ttu-id="3ad71-117">Nastaví zprávu, šifrování a key-wrap algoritmy, které se používají k zajištění zabezpečení na základě zpráv pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3ad71-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="3ad71-118">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="3ad71-118">The default value is `Aes256`.</span></span> <span data-ttu-id="3ad71-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="3ad71-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="3ad71-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3ad71-120">clientCredentialType</span></span>|<span data-ttu-id="3ad71-121">Určuje typ přihlašovacích údajů pro použití při ověřování klientů pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3ad71-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="3ad71-122">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3ad71-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ad71-123">-Žádný: To umožňuje službě komunikovat s anonymní klienty.</span><span class="sxs-lookup"><span data-stu-id="3ad71-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="3ad71-124">Služby ani klienta vyžaduje přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="3ad71-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="3ad71-125">– Windows: To umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="3ad71-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="3ad71-126">To provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="3ad71-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="3ad71-127">-Uživatelské jméno: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="3ad71-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="3ad71-128">Přihlašovací údaje, které v tomto případě musí být zadaná pomocí `clientCredentials` chování **upozornění:**  Odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv Windows Communication Foundation (WCF) není podporována.</span><span class="sxs-lookup"><span data-stu-id="3ad71-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="3ad71-129">Proto WCF vynutí, že při použití pověření uživatelských jmen zabezpečené výměny.</span><span class="sxs-lookup"><span data-stu-id="3ad71-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="3ad71-130">Tento režim vyžaduje, aby byl specifikován certifikát služby na straně klienta pomocí `clientCredential` chování a `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="3ad71-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="3ad71-131">-Certifikátu: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3ad71-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="3ad71-132">Pověření klienta nejsou v tomto případě musí být zadaná pomocí `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="3ad71-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="3ad71-133">Přihlašovací údaje služby v tomto případě musí být zadaná pomocí `clientCredentials` chování tak, že zadáte `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="3ad71-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="3ad71-134">-Služba CardSpace: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí CardSpace.</span><span class="sxs-lookup"><span data-stu-id="3ad71-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="3ad71-135">`serviceCertiifcate` Musí být zřízený v `clientCredential` chování.</span><span class="sxs-lookup"><span data-stu-id="3ad71-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="3ad71-136">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="3ad71-136">The default value is `Windows`.</span></span> <span data-ttu-id="3ad71-137">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3ad71-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ad71-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ad71-138">Child Elements</span></span>  
 <span data-ttu-id="3ad71-139">Žádná</span><span class="sxs-lookup"><span data-stu-id="3ad71-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ad71-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ad71-140">Parent Elements</span></span>  
  
|<span data-ttu-id="3ad71-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ad71-141">Element</span></span>|<span data-ttu-id="3ad71-142">Popis</span><span class="sxs-lookup"><span data-stu-id="3ad71-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ad71-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3ad71-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="3ad71-144">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ad71-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ad71-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ad71-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="3ad71-146">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="3ad71-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="3ad71-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ad71-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3ad71-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="3ad71-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3ad71-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3ad71-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3ad71-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ad71-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3ad71-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ad71-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
