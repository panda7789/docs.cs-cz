---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400500"
---
# <a name="clientcredentials"></a><span data-ttu-id="51adf-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="51adf-101">\<clientCredentials></span></span>
<span data-ttu-id="51adf-102">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="51adf-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
<span data-ttu-id="51adf-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="51adf-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="51adf-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="51adf-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="51adf-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="51adf-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="51adf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="51adf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="51adf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="51adf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="51adf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientCredentials**</span><span class="sxs-lookup"><span data-stu-id="51adf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51adf-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51adf-109">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51adf-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51adf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="51adf-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51adf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51adf-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="51adf-112">Attributes</span></span>  
  
|<span data-ttu-id="51adf-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="51adf-113">Attribute</span></span>|<span data-ttu-id="51adf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="51adf-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="51adf-115">Logická hodnota určující, zda může být interaktivní uživatel zapojen do výběru přihlašovacích údajů klienta za běhu.</span><span class="sxs-lookup"><span data-stu-id="51adf-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="51adf-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="51adf-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="51adf-117">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="51adf-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51adf-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51adf-118">Child Elements</span></span>  
  
|<span data-ttu-id="51adf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="51adf-119">Element</span></span>|<span data-ttu-id="51adf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="51adf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51adf-121">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="51adf-121">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="51adf-122">Určuje certifikát, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="51adf-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="51adf-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="51adf-124">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="51adf-124">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="51adf-125">Určuje výtah, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="51adf-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="51adf-126">Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="51adf-127">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="51adf-127">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="51adf-128">Určuje vlastní typ tokenu, který se používá k ověření klienta ke službě tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="51adf-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="51adf-129">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="51adf-130">\<peer></span><span class="sxs-lookup"><span data-stu-id="51adf-130">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="51adf-131">Určuje aktuální přihlašovací údaje partnerského vztahu.</span><span class="sxs-lookup"><span data-stu-id="51adf-131">Specifies a current peer credential.</span></span> <span data-ttu-id="51adf-132">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="51adf-133">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="51adf-133">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="51adf-134">Určuje certifikát použitý k ověření služby klientovi a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="51adf-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="51adf-135">Tento certifikát musí být dodán od služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="51adf-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="51adf-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="51adf-137">\<windows></span><span class="sxs-lookup"><span data-stu-id="51adf-137">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="51adf-138">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="51adf-138">Specifies a Windows credential.</span></span> <span data-ttu-id="51adf-139">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="51adf-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="51adf-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="51adf-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51adf-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51adf-141">Parent Elements</span></span>  
  
|<span data-ttu-id="51adf-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="51adf-142">Element</span></span>|<span data-ttu-id="51adf-143">Popis</span><span class="sxs-lookup"><span data-stu-id="51adf-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51adf-144">\<> chování</span><span class="sxs-lookup"><span data-stu-id="51adf-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="51adf-145">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="51adf-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51adf-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51adf-146">Remarks</span></span>  
 <span data-ttu-id="51adf-147">Pověření klienta slouží k ověřování klienta se službami v případech, kdy je nutné vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="51adf-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="51adf-148">Tento oddíl konfigurace lze také použít k určení certifikátů služby pro scénáře, ve kterých musí klient zabezpečit zprávy do služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="51adf-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51adf-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51adf-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="51adf-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="51adf-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="51adf-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="51adf-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
