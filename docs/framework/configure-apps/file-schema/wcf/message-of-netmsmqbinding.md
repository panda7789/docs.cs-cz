---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736755"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="4039f-102">\<message> z \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="4039f-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="4039f-103">Definuje nastavení zabezpečení zprávy protokolu SOAP u této `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="4039f-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="4039f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4039f-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="4039f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4039f-105">Attributes and Elements</span></span>

<span data-ttu-id="4039f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4039f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4039f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4039f-107">Attributes</span></span>

|<span data-ttu-id="4039f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4039f-108">Attribute</span></span>|<span data-ttu-id="4039f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4039f-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="4039f-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="4039f-110">algorithmSuite</span></span>|<span data-ttu-id="4039f-111">Nastaví šifrování zprávy a algoritmy pro zabalení klíčů, které se používají k zajištění zabezpečení založeného na zprávách pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4039f-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="4039f-112">Výchozí hodnota je `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="4039f-112">The default value is `Aes256`.</span></span> <span data-ttu-id="4039f-113">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="4039f-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="4039f-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="4039f-114">clientCredentialType</span></span>|<span data-ttu-id="4039f-115">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klienta pro zprávy odesílané prostřednictvím přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4039f-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="4039f-116">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4039f-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4039f-117">-None: umožňuje službě interakci s anonymními klienty.</span><span class="sxs-lookup"><span data-stu-id="4039f-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="4039f-118">Služba ani klient nevyžaduje pověření.</span><span class="sxs-lookup"><span data-stu-id="4039f-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="4039f-119">-Windows: umožňuje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4039f-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="4039f-120">Tato vždy provádí ověřování pomocí protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="4039f-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="4039f-121">-UserName: umožňuje službě vyžadovat, aby byl klient ověřený pomocí přihlašovacích údajů uživatele.</span><span class="sxs-lookup"><span data-stu-id="4039f-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="4039f-122">Přihlašovací údaje v tomto případě je nutné zadat pomocí funkce `clientCredentials` **opatrnosti:** Windows Communication Foundation (WCF) nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="4039f-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="4039f-123">Proto WCF vynutilo, aby při použití přihlašovacích údajů uživatelského jména byla výměna zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="4039f-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="4039f-124">Tento režim vyžaduje, aby se certifikát služby zadal na straně klienta pomocí `clientCredential` chování a `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="4039f-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="4039f-125">-Certificate: umožňuje službě vyžadovat, aby byl klient ověřený pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4039f-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="4039f-126">Pověření klienta v tomto případě je nutné zadat pomocí `clientCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="4039f-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="4039f-127">Pověření služby v tomto případě je nutné zadat pomocí `clientCredentials` chování zadáním `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="4039f-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="4039f-128">-Služba CardSpace: umožňuje službě, aby vyžadovala ověření klienta pomocí služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="4039f-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="4039f-129">Je `serviceCertificate` nutné zřídit v `clientCredential` chování.</span><span class="sxs-lookup"><span data-stu-id="4039f-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="4039f-130">Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="4039f-130">The default value is `Windows`.</span></span> <span data-ttu-id="4039f-131">Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4039f-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4039f-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4039f-132">Child Elements</span></span>

<span data-ttu-id="4039f-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="4039f-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4039f-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4039f-134">Parent Elements</span></span>

|<span data-ttu-id="4039f-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="4039f-135">Element</span></span>|<span data-ttu-id="4039f-136">Description</span><span class="sxs-lookup"><span data-stu-id="4039f-136">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="4039f-137">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4039f-137">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4039f-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4039f-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="4039f-139">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="4039f-139">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="4039f-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4039f-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4039f-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="4039f-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4039f-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4039f-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4039f-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4039f-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
