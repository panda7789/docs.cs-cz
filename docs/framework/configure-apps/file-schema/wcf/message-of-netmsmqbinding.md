---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 09d9d4a5d1967afaf9a6ed5756c309e78fee0923
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400260"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="768dc-102">\<> zpráv > \<NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="768dc-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="768dc-103">Definuje nastavení zabezpečení zprávy protokolu SOAP u této `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="768dc-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="768dc-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="768dc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="768dc-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="768dc-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="768dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="768dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="768dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="768dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="768dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="768dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="768dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="768dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="768dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zprávy**</span><span class="sxs-lookup"><span data-stu-id="768dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="768dc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="768dc-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="768dc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="768dc-112">Attributes and Elements</span></span>

<span data-ttu-id="768dc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="768dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="768dc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="768dc-114">Attributes</span></span>

|<span data-ttu-id="768dc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="768dc-115">Attribute</span></span>|<span data-ttu-id="768dc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="768dc-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="768dc-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="768dc-117">algorithmSuite</span></span>|<span data-ttu-id="768dc-118">Nastaví šifrování zprávy a algoritmy pro zabalení klíčů, které se používají k zajištění zabezpečení založeného na zprávách pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="768dc-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="768dc-119">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="768dc-119">The default value is `Aes256`.</span></span> <span data-ttu-id="768dc-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="768dc-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="768dc-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="768dc-121">clientCredentialType</span></span>|<span data-ttu-id="768dc-122">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klienta pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="768dc-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="768dc-123">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="768dc-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="768dc-124">NTato Díky tomu může služba spolupracovat s anonymními klienty.</span><span class="sxs-lookup"><span data-stu-id="768dc-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="768dc-125">Služba ani klient nevyžaduje pověření.</span><span class="sxs-lookup"><span data-stu-id="768dc-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="768dc-126">Systému To umožňuje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="768dc-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="768dc-127">Tato vždy provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="768dc-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="768dc-128">Jmen Díky tomu může služba vyžadovat, aby se klient ověřil pomocí přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="768dc-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="768dc-129">Přihlašovací údaje v tomto případě je potřeba zadat pomocí upozornění na `clientCredentials` chování **:**  Windows Communication Foundation (WCF) nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="768dc-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="768dc-130">Proto WCF vynutilo, aby při použití přihlašovacích údajů uživatelského jména byla výměna zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="768dc-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="768dc-131">Tento režim vyžaduje, aby se certifikát služby zadal na straně klienta pomocí `clientCredential` chování a. `serviceCertificate`</span><span class="sxs-lookup"><span data-stu-id="768dc-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="768dc-132">Certifikát Díky tomu může služba vyžadovat, aby byl klient ověřený pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="768dc-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="768dc-133">Pověření klienta v tomto případě je nutné zadat pomocí `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="768dc-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="768dc-134">Pověření služby v tomto případě je nutné zadat pomocí `clientCredentials` chování `serviceCertificate`zadáním.</span><span class="sxs-lookup"><span data-stu-id="768dc-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="768dc-135">Službu Díky tomu může služba vyžadovat, aby byl klient ověřený pomocí služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="768dc-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="768dc-136">Je nutné zřídit `clientCredential`vchování. `serviceCertificate`</span><span class="sxs-lookup"><span data-stu-id="768dc-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="768dc-137">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="768dc-137">The default value is `Windows`.</span></span> <span data-ttu-id="768dc-138">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="768dc-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="768dc-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="768dc-139">Child Elements</span></span>

<span data-ttu-id="768dc-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="768dc-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="768dc-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="768dc-141">Parent Elements</span></span>

|<span data-ttu-id="768dc-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="768dc-142">Element</span></span>|<span data-ttu-id="768dc-143">Popis</span><span class="sxs-lookup"><span data-stu-id="768dc-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="768dc-144">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="768dc-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="768dc-145">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="768dc-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="768dc-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="768dc-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="768dc-147">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="768dc-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="768dc-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="768dc-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="768dc-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="768dc-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="768dc-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="768dc-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="768dc-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="768dc-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="768dc-152">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="768dc-152">\<binding></span></span>](../../../misc/binding.md)
