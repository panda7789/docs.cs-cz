---
title: "&lt;message&gt; – &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdef94f5ee570d7ce93544950a5a290d3eb534f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="99c84-102">&lt;message&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="99c84-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="99c84-103">Definuje nastavení zabezpečení protokolu SOAP zprávy na tomto `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="99c84-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="99c84-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="99c84-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="99c84-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="99c84-105">\<bindings></span></span>  
<span data-ttu-id="99c84-106">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="99c84-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="99c84-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="99c84-107">\<binding></span></span>  
<span data-ttu-id="99c84-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="99c84-108">\<security></span></span>  
<span data-ttu-id="99c84-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="99c84-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c84-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99c84-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c84-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99c84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="99c84-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99c84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c84-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="99c84-113">Attributes</span></span>  
  
|<span data-ttu-id="99c84-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="99c84-114">Attribute</span></span>|<span data-ttu-id="99c84-115">Popis</span><span class="sxs-lookup"><span data-stu-id="99c84-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99c84-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="99c84-116">algorithmSuite</span></span>|<span data-ttu-id="99c84-117">Nastaví zprávu algoritmy šifrování a klíč wrap, které se používají k dosažení zabezpečení na základě zpráv pro zprávy odeslané přes přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="99c84-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="99c84-118">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="99c84-118">The default value is `Aes256`.</span></span> <span data-ttu-id="99c84-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="99c84-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="99c84-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="99c84-120">clientCredentialType</span></span>|<span data-ttu-id="99c84-121">Určuje typ pověření, který se má použít při ověřování klienta pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="99c84-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="99c84-122">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="99c84-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="99c84-123">-None: To umožňuje službu k interakci s anonymní klienty.</span><span class="sxs-lookup"><span data-stu-id="99c84-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="99c84-124">Služba ani klient vyžaduje přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="99c84-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="99c84-125">-Windows: Umožňuje výměnu SOAP pod pro ověřený kontext pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="99c84-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="99c84-126">Vždy provede ověřování založené na protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="99c84-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="99c84-127">-UserName: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="99c84-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="99c84-128">Přihlašovací údaje v takovém případě musí být zadán pomocí `clientCredentials` chování **upozornění:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nepodporuje odesílání heslo hodnotou hash nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="99c84-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="99c84-129">Proto [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vynutí, že exchange zabezpečené při použití pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="99c84-129">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="99c84-130">Tento režim vyžaduje, aby byl certifikát služby specifikován na straně klienta používá `clientCredential` chování a `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="99c84-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="99c84-131">-Certifikát: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="99c84-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="99c84-132">V takovém případě musí být zadán pomocí pověření klienta `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="99c84-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="99c84-133">Přihlašovací údaje služby v takovém případě musí být zadán pomocí `clientCredentials` chování zadáním `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="99c84-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="99c84-134">-CardSpace: To umožňuje službě vyžadují, ověření klienta pomocí CardSpace.</span><span class="sxs-lookup"><span data-stu-id="99c84-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="99c84-135">`serviceCertiifcate` Musí být zřízená v `clientCredential` chování.</span><span class="sxs-lookup"><span data-stu-id="99c84-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="99c84-136">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="99c84-136">The default value is `Windows`.</span></span> <span data-ttu-id="99c84-137">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="99c84-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99c84-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99c84-138">Child Elements</span></span>  
 <span data-ttu-id="99c84-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="99c84-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99c84-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99c84-140">Parent Elements</span></span>  
  
|<span data-ttu-id="99c84-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="99c84-141">Element</span></span>|<span data-ttu-id="99c84-142">Popis</span><span class="sxs-lookup"><span data-stu-id="99c84-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c84-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="99c84-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="99c84-144">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="99c84-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99c84-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="99c84-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="99c84-146">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="99c84-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="99c84-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="99c84-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="99c84-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="99c84-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="99c84-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="99c84-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="99c84-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="99c84-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="99c84-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="99c84-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
