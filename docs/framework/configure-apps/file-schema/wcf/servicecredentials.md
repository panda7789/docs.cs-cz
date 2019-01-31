---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 54ac4f0aa31a4311976449d545880d825c06337d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256469"
---
# <a name="servicecredentials"></a><span data-ttu-id="2e590-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2e590-101">\<serviceCredentials></span></span>
<span data-ttu-id="2e590-102">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="2e590-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="2e590-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e590-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e590-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2e590-104">\<behaviors></span></span>  
<span data-ttu-id="2e590-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2e590-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2e590-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2e590-106">\<behavior></span></span>  
<span data-ttu-id="2e590-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2e590-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e590-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e590-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e590-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e590-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e590-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e590-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e590-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e590-111">Attributes</span></span>  
  
|<span data-ttu-id="2e590-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2e590-112">Attribute</span></span>|<span data-ttu-id="2e590-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2e590-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2e590-114">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="2e590-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e590-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e590-115">Child Elements</span></span>  
  
|<span data-ttu-id="2e590-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e590-116">Element</span></span>|<span data-ttu-id="2e590-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2e590-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e590-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="2e590-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="2e590-119">Určuje certifikát, který chcete použít, pokud je k dispozici out-of-band klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="2e590-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="2e590-120">Tento prvek určuje také nastavení ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="2e590-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="2e590-121">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="2e590-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e590-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="2e590-123">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="2e590-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="2e590-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="2e590-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="2e590-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="2e590-126">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="2e590-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="2e590-127">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="2e590-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e590-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="2e590-129">Určuje aktuální pověření pro zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="2e590-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="2e590-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="2e590-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2e590-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="2e590-132">Určuje certifikát používaný službou identifikovat.</span><span class="sxs-lookup"><span data-stu-id="2e590-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="2e590-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="2e590-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e590-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="2e590-135">Určuje nastavení pro ověření uživatelského jména hesla.</span><span class="sxs-lookup"><span data-stu-id="2e590-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="2e590-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="2e590-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="2e590-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="2e590-138">Určuje nastavení pro ověřování přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="2e590-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="2e590-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2e590-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e590-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e590-140">Parent Elements</span></span>  
  
|<span data-ttu-id="2e590-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e590-141">Element</span></span>|<span data-ttu-id="2e590-142">Popis</span><span class="sxs-lookup"><span data-stu-id="2e590-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e590-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2e590-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2e590-144">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2e590-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e590-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e590-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="2e590-146">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2e590-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
