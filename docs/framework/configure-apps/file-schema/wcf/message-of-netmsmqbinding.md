---
title: '&lt;message&gt; – &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 65a8b0fa120d23931ad218ac67846c066b050af8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402241"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="8bbbc-102">&lt;message&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8bbbc-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="8bbbc-103">Definuje nastavení založená na protokolu SOAP zprávy zabezpečení v tomto `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="8bbbc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8bbbc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8bbbc-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-105">\<bindings></span></span>  
<span data-ttu-id="8bbbc-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="8bbbc-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-107">\<binding></span></span>  
<span data-ttu-id="8bbbc-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-108">\<security></span></span>  
<span data-ttu-id="8bbbc-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bbbc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bbbc-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bbbc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8bbbc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8bbbc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bbbc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8bbbc-113">Attributes</span></span>  
  
|<span data-ttu-id="8bbbc-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="8bbbc-114">Attribute</span></span>|<span data-ttu-id="8bbbc-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8bbbc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bbbc-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="8bbbc-116">algorithmSuite</span></span>|<span data-ttu-id="8bbbc-117">Nastaví zprávu, šifrování a key-wrap algoritmy, které se používají k zajištění zabezpečení na základě zpráv pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="8bbbc-118">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-118">The default value is `Aes256`.</span></span> <span data-ttu-id="8bbbc-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="8bbbc-120">Typ clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8bbbc-120">clientCredentialType</span></span>|<span data-ttu-id="8bbbc-121">Určuje typ přihlašovacích údajů pro použití při ověřování klientů pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="8bbbc-122">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="8bbbc-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8bbbc-123">-Žádný: To umožňuje službě komunikovat s anonymní klienty.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="8bbbc-124">Služby ani klienta vyžaduje přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="8bbbc-125">-Windows: Umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů pro Windows.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="8bbbc-126">To provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="8bbbc-127">-UserName: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="8bbbc-128">Přihlašovací údaje, které v tomto případě musí být zadaná pomocí `clientCredentials` chování **upozornění:** Windows Communication Foundation (WCF) nepodporuje odesílání hodnotou hash nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro heslo zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="8bbbc-129">Proto WCF vynutí, že při použití pověření uživatelských jmen zabezpečené výměny.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="8bbbc-130">Tento režim vyžaduje, aby byl specifikován certifikát služby na straně klienta pomocí `clientCredential` chování a `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="8bbbc-131">-Certificate: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="8bbbc-132">Pověření klienta nejsou v tomto případě musí být zadaná pomocí `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="8bbbc-133">Přihlašovací údaje služby v tomto případě musí být zadaná pomocí `clientCredentials` chování tak, že zadáte `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="8bbbc-134">-Služba CardSpace: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí CardSpace.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="8bbbc-135">`serviceCertiifcate` Musí být zřízený v `clientCredential` chování.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="8bbbc-136">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-136">The default value is `Windows`.</span></span> <span data-ttu-id="8bbbc-137">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bbbc-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8bbbc-138">Child Elements</span></span>  
 <span data-ttu-id="8bbbc-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="8bbbc-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bbbc-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8bbbc-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8bbbc-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="8bbbc-141">Element</span></span>|<span data-ttu-id="8bbbc-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8bbbc-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bbbc-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="8bbbc-144">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="8bbbc-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bbbc-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bbbc-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="8bbbc-146">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="8bbbc-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="8bbbc-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8bbbc-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8bbbc-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="8bbbc-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8bbbc-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8bbbc-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8bbbc-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="8bbbc-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8bbbc-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8bbbc-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
