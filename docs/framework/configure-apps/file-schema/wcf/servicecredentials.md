---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670284"
---
# <a name="servicecredentials"></a><span data-ttu-id="0bf84-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="0bf84-101">\<serviceCredentials></span></span>
<span data-ttu-id="0bf84-102">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="0bf84-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="0bf84-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0bf84-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0bf84-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0bf84-104">\<behaviors></span></span>  
<span data-ttu-id="0bf84-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0bf84-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0bf84-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0bf84-106">\<behavior></span></span>  
<span data-ttu-id="0bf84-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="0bf84-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf84-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf84-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bf84-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0bf84-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0bf84-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0bf84-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bf84-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0bf84-111">Attributes</span></span>  
  
|<span data-ttu-id="0bf84-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="0bf84-112">Attribute</span></span>|<span data-ttu-id="0bf84-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf84-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0bf84-114">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="0bf84-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bf84-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0bf84-115">Child Elements</span></span>  
  
|<span data-ttu-id="0bf84-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="0bf84-116">Element</span></span>|<span data-ttu-id="0bf84-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf84-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bf84-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="0bf84-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="0bf84-119">Určuje certifikát, který chcete použít, pokud je k dispozici out-of-band klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="0bf84-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="0bf84-120">Tento prvek určuje také nastavení ověřování certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="0bf84-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="0bf84-121">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="0bf84-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="0bf84-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="0bf84-123">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="0bf84-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="0bf84-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="0bf84-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="0bf84-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="0bf84-126">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="0bf84-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="0bf84-127">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="0bf84-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="0bf84-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="0bf84-129">Určuje aktuální pověření pro zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="0bf84-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="0bf84-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="0bf84-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="0bf84-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="0bf84-132">Určuje certifikát používaný službou identifikovat.</span><span class="sxs-lookup"><span data-stu-id="0bf84-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="0bf84-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="0bf84-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="0bf84-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="0bf84-135">Určuje nastavení pro ověření uživatelského jména hesla.</span><span class="sxs-lookup"><span data-stu-id="0bf84-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="0bf84-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="0bf84-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="0bf84-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="0bf84-138">Určuje nastavení pro ověřování přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="0bf84-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="0bf84-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0bf84-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bf84-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0bf84-140">Parent Elements</span></span>  
  
|<span data-ttu-id="0bf84-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="0bf84-141">Element</span></span>|<span data-ttu-id="0bf84-142">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf84-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bf84-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0bf84-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="0bf84-144">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="0bf84-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bf84-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bf84-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="0bf84-146">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0bf84-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
