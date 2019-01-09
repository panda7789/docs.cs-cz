---
title: '&lt;ServiceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b9e32509a5e182301455eaf0e602a03c51fbc23a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150770"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="00d8e-102">&lt;ServiceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="00d8e-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="00d8e-103">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="00d8e-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="00d8e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="00d8e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="00d8e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="00d8e-105">\<behaviors></span></span>  
<span data-ttu-id="00d8e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="00d8e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="00d8e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="00d8e-107">\<behavior></span></span>  
<span data-ttu-id="00d8e-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="00d8e-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d8e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d8e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00d8e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00d8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="00d8e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00d8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00d8e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="00d8e-112">Attributes</span></span>  
  
|<span data-ttu-id="00d8e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="00d8e-113">Attribute</span></span>|<span data-ttu-id="00d8e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8e-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="00d8e-115">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="00d8e-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00d8e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00d8e-116">Child Elements</span></span>  
  
|<span data-ttu-id="00d8e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="00d8e-117">Element</span></span>|<span data-ttu-id="00d8e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00d8e-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="00d8e-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="00d8e-120">Určuje certifikát, který chcete použít, pokud je k dispozici out-of-band klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="00d8e-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="00d8e-121">Tento prvek určuje také nastavení ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="00d8e-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="00d8e-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="00d8e-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="00d8e-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="00d8e-124">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="00d8e-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="00d8e-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="00d8e-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="00d8e-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="00d8e-127">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="00d8e-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="00d8e-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="00d8e-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="00d8e-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="00d8e-130">Určuje aktuální pověření pro zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="00d8e-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="00d8e-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="00d8e-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="00d8e-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="00d8e-133">Určuje certifikát používaný službou identifikovat.</span><span class="sxs-lookup"><span data-stu-id="00d8e-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="00d8e-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="00d8e-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="00d8e-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="00d8e-136">Určuje nastavení pro ověření uživatelského jména hesla.</span><span class="sxs-lookup"><span data-stu-id="00d8e-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="00d8e-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="00d8e-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="00d8e-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="00d8e-139">Určuje nastavení pro ověřování přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="00d8e-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="00d8e-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="00d8e-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00d8e-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00d8e-141">Parent Elements</span></span>  
  
|<span data-ttu-id="00d8e-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="00d8e-142">Element</span></span>|<span data-ttu-id="00d8e-143">Popis</span><span class="sxs-lookup"><span data-stu-id="00d8e-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00d8e-144">\<chování ></span><span class="sxs-lookup"><span data-stu-id="00d8e-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="00d8e-145">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="00d8e-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00d8e-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d8e-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="00d8e-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="00d8e-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
