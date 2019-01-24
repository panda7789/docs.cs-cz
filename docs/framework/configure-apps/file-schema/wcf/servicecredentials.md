---
title: '&lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 978439dfeb0c5275e2ec43f9c891b6927e7a7869
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610432"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="808f0-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="808f0-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="808f0-103">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="808f0-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="808f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="808f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="808f0-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="808f0-105">\<behaviors></span></span>  
<span data-ttu-id="808f0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="808f0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="808f0-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="808f0-107">\<behavior></span></span>  
<span data-ttu-id="808f0-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="808f0-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="808f0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="808f0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="808f0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="808f0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="808f0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="808f0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="808f0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="808f0-112">Attributes</span></span>  
  
|<span data-ttu-id="808f0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="808f0-113">Attribute</span></span>|<span data-ttu-id="808f0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="808f0-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="808f0-115">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="808f0-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="808f0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="808f0-116">Child Elements</span></span>  
  
|<span data-ttu-id="808f0-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="808f0-117">Element</span></span>|<span data-ttu-id="808f0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="808f0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="808f0-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="808f0-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="808f0-120">Určuje certifikát, který chcete použít, pokud je k dispozici out-of-band klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="808f0-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="808f0-121">Tento prvek určuje také nastavení ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="808f0-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="808f0-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="808f0-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="808f0-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="808f0-124">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="808f0-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="808f0-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="808f0-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="808f0-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="808f0-127">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="808f0-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="808f0-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="808f0-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="808f0-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="808f0-130">Určuje aktuální pověření pro zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="808f0-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="808f0-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="808f0-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="808f0-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="808f0-133">Určuje certifikát používaný službou identifikovat.</span><span class="sxs-lookup"><span data-stu-id="808f0-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="808f0-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="808f0-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="808f0-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="808f0-136">Určuje nastavení pro ověření uživatelského jména hesla.</span><span class="sxs-lookup"><span data-stu-id="808f0-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="808f0-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="808f0-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="808f0-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="808f0-139">Určuje nastavení pro ověřování přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="808f0-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="808f0-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="808f0-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="808f0-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="808f0-141">Parent Elements</span></span>  
  
|<span data-ttu-id="808f0-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="808f0-142">Element</span></span>|<span data-ttu-id="808f0-143">Popis</span><span class="sxs-lookup"><span data-stu-id="808f0-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="808f0-144">\<behavior></span><span class="sxs-lookup"><span data-stu-id="808f0-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="808f0-145">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="808f0-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="808f0-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="808f0-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="808f0-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="808f0-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
