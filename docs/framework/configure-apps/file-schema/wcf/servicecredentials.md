---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936301"
---
# <a name="servicecredentials"></a><span data-ttu-id="e0902-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e0902-101">\<serviceCredentials></span></span>
<span data-ttu-id="e0902-102">Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="e0902-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="e0902-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e0902-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0902-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e0902-104">\<behaviors></span></span>  
<span data-ttu-id="e0902-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e0902-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e0902-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e0902-106">\<behavior></span></span>  
<span data-ttu-id="e0902-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e0902-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0902-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0902-108">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0902-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e0902-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e0902-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e0902-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0902-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e0902-111">Attributes</span></span>  
  
|<span data-ttu-id="e0902-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e0902-112">Attribute</span></span>|<span data-ttu-id="e0902-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e0902-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e0902-114">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="e0902-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0902-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e0902-115">Child Elements</span></span>  
  
|<span data-ttu-id="e0902-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="e0902-116">Element</span></span>|<span data-ttu-id="e0902-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e0902-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0902-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="e0902-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e0902-119">Určuje certifikát, který má být použit v případě, že je klientský certifikát k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="e0902-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="e0902-120">Tento prvek také určuje nastavení ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e0902-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="e0902-121">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="e0902-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="e0902-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="e0902-123">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="e0902-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="e0902-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="e0902-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="e0902-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="e0902-126">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="e0902-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="e0902-127">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="e0902-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="e0902-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="e0902-129">Určuje aktuální pověření pro zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="e0902-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="e0902-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="e0902-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e0902-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="e0902-132">Určuje certifikát používaný službou k identifikaci sebe sama.</span><span class="sxs-lookup"><span data-stu-id="e0902-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="e0902-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="e0902-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="e0902-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="e0902-135">Určuje nastavení pro ověřování hesla uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="e0902-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="e0902-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="e0902-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="e0902-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="e0902-138">Určuje nastavení pro ověření přihlašovacích údajů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e0902-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="e0902-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e0902-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0902-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e0902-140">Parent Elements</span></span>  
  
|<span data-ttu-id="e0902-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="e0902-141">Element</span></span>|<span data-ttu-id="e0902-142">Popis</span><span class="sxs-lookup"><span data-stu-id="e0902-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0902-143">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e0902-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e0902-144">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e0902-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0902-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0902-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="e0902-146">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e0902-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
