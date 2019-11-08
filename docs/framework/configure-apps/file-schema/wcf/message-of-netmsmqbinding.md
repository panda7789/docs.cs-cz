---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736755"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="fe3e0-102">\<> zprávy \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="fe3e0-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="fe3e0-103">Definuje nastavení zabezpečení zprávy protokolu SOAP u této `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="fe3e0-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fe3e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe3e0-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="fe3e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fe3e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fe3e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fe3e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fe3e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="fe3e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="fe3e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fe3e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fe3e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="fe3e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**</span><span class="sxs-lookup"><span data-stu-id="fe3e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="fe3e0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe3e0-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fe3e0-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe3e0-112">Attributes and Elements</span></span>

<span data-ttu-id="fe3e0-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe3e0-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe3e0-114">Attributes</span></span>

|<span data-ttu-id="fe3e0-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe3e0-115">Attribute</span></span>|<span data-ttu-id="fe3e0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fe3e0-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fe3e0-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="fe3e0-117">algorithmSuite</span></span>|<span data-ttu-id="fe3e0-118">Nastaví šifrování zprávy a algoritmy pro zabalení klíčů, které se používají k zajištění zabezpečení založeného na zprávách pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="fe3e0-119">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-119">The default value is `Aes256`.</span></span> <span data-ttu-id="fe3e0-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="fe3e0-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="fe3e0-121">clientCredentialType</span></span>|<span data-ttu-id="fe3e0-122">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klienta pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="fe3e0-123">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="fe3e0-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fe3e0-124">-None: umožňuje službě interakci s anonymními klienty.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="fe3e0-125">Služba ani klient nevyžaduje pověření.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="fe3e0-126">-Windows: umožňuje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="fe3e0-127">Tato vždy provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="fe3e0-128">-UserName: umožňuje službě vyžadovat, aby byl klient ověřený pomocí přihlašovacích údajů uživatele.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="fe3e0-129">Přihlašovací údaje v tomto případě je potřeba zadat pomocí `clientCredentials` chování při **:** Windows Communication Foundation (WCF) nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="fe3e0-130">Proto WCF vynutilo, aby při použití přihlašovacích údajů uživatelského jména byla výměna zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="fe3e0-131">Tento režim vyžaduje, aby se certifikát služby zadal na straně klienta pomocí `clientCredential` chování a `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="fe3e0-132">-Certificate: umožňuje službě vyžadovat, aby byl klient ověřený pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="fe3e0-133">Přihlašovací údaje klienta v tomto případě je potřeba zadat pomocí chování `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="fe3e0-134">Pověření služby v tomto případě je nutné zadat pomocí `clientCredentials` chování zadáním `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="fe3e0-135">-Služba CardSpace: umožňuje službě, aby vyžadovala ověření klienta pomocí služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="fe3e0-136">`serviceCertificate` musí být zřízené v chování `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="fe3e0-137">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-137">The default value is `Windows`.</span></span> <span data-ttu-id="fe3e0-138">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fe3e0-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe3e0-139">Child Elements</span></span>

<span data-ttu-id="fe3e0-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe3e0-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe3e0-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe3e0-141">Parent Elements</span></span>

|<span data-ttu-id="fe3e0-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe3e0-142">Element</span></span>|<span data-ttu-id="fe3e0-143">Popis</span><span class="sxs-lookup"><span data-stu-id="fe3e0-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe3e0-144">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="fe3e0-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="fe3e0-145">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="fe3e0-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fe3e0-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe3e0-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="fe3e0-147">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="fe3e0-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fe3e0-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fe3e0-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fe3e0-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="fe3e0-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fe3e0-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="fe3e0-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fe3e0-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fe3e0-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fe3e0-152">vazba \<</span><span class="sxs-lookup"><span data-stu-id="fe3e0-152">\<binding></span></span>](bindings.md)
