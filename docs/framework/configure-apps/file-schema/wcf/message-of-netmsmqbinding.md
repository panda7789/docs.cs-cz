---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931520"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="59b9d-102">\<> zpráv > \<NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="59b9d-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="59b9d-103">Definuje nastavení zabezpečení zprávy protokolu SOAP u této `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="59b9d-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="59b9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59b9d-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="59b9d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59b9d-105">Attributes and Elements</span></span>

<span data-ttu-id="59b9d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59b9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="59b9d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="59b9d-107">Attributes</span></span>

|<span data-ttu-id="59b9d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="59b9d-108">Attribute</span></span>|<span data-ttu-id="59b9d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="59b9d-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="59b9d-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="59b9d-110">algorithmSuite</span></span>|<span data-ttu-id="59b9d-111">Nastaví šifrování zprávy a algoritmy pro zabalení klíčů, které se používají k zajištění zabezpečení založeného na zprávách pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="59b9d-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="59b9d-112">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="59b9d-112">The default value is `Aes256`.</span></span> <span data-ttu-id="59b9d-113">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="59b9d-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="59b9d-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="59b9d-114">clientCredentialType</span></span>|<span data-ttu-id="59b9d-115">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klienta pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="59b9d-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="59b9d-116">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="59b9d-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59b9d-117">NTato Díky tomu může služba spolupracovat s anonymními klienty.</span><span class="sxs-lookup"><span data-stu-id="59b9d-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="59b9d-118">Služba ani klient nevyžaduje pověření.</span><span class="sxs-lookup"><span data-stu-id="59b9d-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="59b9d-119">Systému To umožňuje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59b9d-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="59b9d-120">Tato vždy provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="59b9d-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="59b9d-121">Jmen Díky tomu může služba vyžadovat, aby se klient ověřil pomocí přihlašovacích údajů uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="59b9d-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="59b9d-122">Přihlašovací údaje v tomto případě je potřeba zadat pomocí upozornění na `clientCredentials` chování **:**  Windows Communication Foundation (WCF) nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="59b9d-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="59b9d-123">Proto WCF vynutilo, aby při použití přihlašovacích údajů uživatelského jména byla výměna zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="59b9d-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="59b9d-124">Tento režim vyžaduje, aby se certifikát služby zadal na straně klienta pomocí `clientCredential` chování a. `serviceCertificate`</span><span class="sxs-lookup"><span data-stu-id="59b9d-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="59b9d-125">Certifikát Díky tomu může služba vyžadovat, aby byl klient ověřený pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="59b9d-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="59b9d-126">Pověření klienta v tomto případě je nutné zadat pomocí `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="59b9d-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="59b9d-127">Pověření služby v tomto případě je nutné zadat pomocí `clientCredentials` chování `serviceCertificate`zadáním.</span><span class="sxs-lookup"><span data-stu-id="59b9d-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="59b9d-128">Službu Díky tomu může služba vyžadovat, aby byl klient ověřený pomocí služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="59b9d-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="59b9d-129">Je nutné zřídit `clientCredential`vchování. `serviceCertificate`</span><span class="sxs-lookup"><span data-stu-id="59b9d-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="59b9d-130">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="59b9d-130">The default value is `Windows`.</span></span> <span data-ttu-id="59b9d-131">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="59b9d-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="59b9d-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59b9d-132">Child Elements</span></span>

<span data-ttu-id="59b9d-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="59b9d-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59b9d-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59b9d-134">Parent Elements</span></span>

|<span data-ttu-id="59b9d-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="59b9d-135">Element</span></span>|<span data-ttu-id="59b9d-136">Popis</span><span class="sxs-lookup"><span data-stu-id="59b9d-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59b9d-137">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="59b9d-137">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="59b9d-138">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="59b9d-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="59b9d-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59b9d-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="59b9d-140">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="59b9d-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="59b9d-141">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59b9d-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="59b9d-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="59b9d-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59b9d-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="59b9d-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59b9d-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59b9d-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="59b9d-145">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59b9d-145">\<binding></span></span>](../../../misc/binding.md)
