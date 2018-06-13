---
title: '&lt;message&gt; – &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e947667c414079f24398b401456efd56bf9922c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358554"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="cf19d-102">&lt;message&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cf19d-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="cf19d-103">Definuje nastavení zabezpečení protokolu SOAP zprávy na tomto `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="cf19d-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="cf19d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf19d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf19d-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cf19d-105">\<bindings></span></span>  
<span data-ttu-id="cf19d-106">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="cf19d-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="cf19d-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cf19d-107">\<binding></span></span>  
<span data-ttu-id="cf19d-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cf19d-108">\<security></span></span>  
<span data-ttu-id="cf19d-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="cf19d-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf19d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf19d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf19d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf19d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf19d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf19d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf19d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf19d-113">Attributes</span></span>  
  
|<span data-ttu-id="cf19d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="cf19d-114">Attribute</span></span>|<span data-ttu-id="cf19d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cf19d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf19d-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="cf19d-116">algorithmSuite</span></span>|<span data-ttu-id="cf19d-117">Nastaví zprávu algoritmy šifrování a klíč wrap, které se používají k dosažení zabezpečení na základě zpráv pro zprávy odeslané přes přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cf19d-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="cf19d-118">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="cf19d-118">The default value is `Aes256`.</span></span> <span data-ttu-id="cf19d-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="cf19d-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="cf19d-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cf19d-120">clientCredentialType</span></span>|<span data-ttu-id="cf19d-121">Určuje typ pověření, který se má použít při ověřování klienta pro zprávy odeslané přes přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cf19d-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="cf19d-122">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="cf19d-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cf19d-123">-None: To umožňuje službu k interakci s anonymní klienty.</span><span class="sxs-lookup"><span data-stu-id="cf19d-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="cf19d-124">Služba ani klient vyžaduje přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="cf19d-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="cf19d-125">-Windows: Umožňuje výměnu SOAP pod pro ověřený kontext pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cf19d-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="cf19d-126">Vždy provede ověřování založené na protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="cf19d-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="cf19d-127">-UserName: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="cf19d-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="cf19d-128">Přihlašovací údaje v takovém případě musí být zadán pomocí `clientCredentials` chování **upozornění:** Windows Communication Foundation (WCF) nepodporuje odesílání hodnotou hash nebo odvozování klíče pomocí hesla a pomocí těchto klíčů pro heslo zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="cf19d-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="cf19d-129">Proto WCF vynutí, že exchange zabezpečené při použití pověření uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="cf19d-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="cf19d-130">Tento režim vyžaduje, aby byl certifikát služby specifikován na straně klienta používá `clientCredential` chování a `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="cf19d-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="cf19d-131">-Certifikát: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="cf19d-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="cf19d-132">V takovém případě musí být zadán pomocí pověření klienta `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="cf19d-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="cf19d-133">Přihlašovací údaje služby v takovém případě musí být zadán pomocí `clientCredentials` chování zadáním `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="cf19d-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="cf19d-134">-CardSpace: To umožňuje službě vyžadují, ověření klienta pomocí CardSpace.</span><span class="sxs-lookup"><span data-stu-id="cf19d-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="cf19d-135">`serviceCertiifcate` Musí být zřízená v `clientCredential` chování.</span><span class="sxs-lookup"><span data-stu-id="cf19d-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="cf19d-136">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="cf19d-136">The default value is `Windows`.</span></span> <span data-ttu-id="cf19d-137">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="cf19d-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf19d-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cf19d-138">Child Elements</span></span>  
 <span data-ttu-id="cf19d-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf19d-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf19d-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cf19d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="cf19d-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf19d-141">Element</span></span>|<span data-ttu-id="cf19d-142">Popis</span><span class="sxs-lookup"><span data-stu-id="cf19d-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf19d-143">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cf19d-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="cf19d-144">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="cf19d-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf19d-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf19d-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="cf19d-146">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="cf19d-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="cf19d-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cf19d-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cf19d-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="cf19d-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cf19d-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cf19d-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cf19d-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="cf19d-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cf19d-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cf19d-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
