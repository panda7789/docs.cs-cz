---
title: '&lt;– serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: a3d63e3d01c009834717a80a9ed9536fd1bdf838
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750398"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="d112a-102">&lt;– serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="d112a-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="d112a-103">Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="d112a-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="d112a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d112a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d112a-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d112a-105">\<behaviors></span></span>  
<span data-ttu-id="d112a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d112a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d112a-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d112a-107">\<behavior></span></span>  
<span data-ttu-id="d112a-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d112a-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d112a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d112a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d112a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d112a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d112a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d112a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d112a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d112a-112">Attributes</span></span>  
  
|<span data-ttu-id="d112a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d112a-113">Attribute</span></span>|<span data-ttu-id="d112a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d112a-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d112a-115">Řetězec, který určuje typ tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d112a-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d112a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d112a-116">Child Elements</span></span>  
  
|<span data-ttu-id="d112a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d112a-117">Element</span></span>|<span data-ttu-id="d112a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d112a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d112a-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="d112a-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="d112a-120">Určuje certifikát, který chcete použít, pokud je k dispozici out-of-band klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="d112a-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="d112a-121">Tento element také určuje nastavení ověření certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="d112a-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="d112a-122">Tento element je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="d112a-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d112a-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="d112a-124">Určuje aktuální vystavený token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="d112a-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="d112a-125">Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="d112a-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="d112a-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="d112a-127">Určuje, že aktuální přihlašovací údaje pro uzel sdílené.</span><span class="sxs-lookup"><span data-stu-id="d112a-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="d112a-128">Tento element je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="d112a-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d112a-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="d112a-130">Určuje, že aktuální přihlašovací údaje pro zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="d112a-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="d112a-131">Tento element je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="d112a-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="d112a-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="d112a-133">Určuje certifikát používají službu identifikovat.</span><span class="sxs-lookup"><span data-stu-id="d112a-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="d112a-134">Tento element je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="d112a-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d112a-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="d112a-136">Určuje nastavení pro ověření hesla uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="d112a-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="d112a-137">Tento element je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="d112a-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d112a-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="d112a-139">Určuje nastavení pro ověření přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="d112a-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="d112a-140">Tento element je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d112a-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d112a-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d112a-141">Parent Elements</span></span>  
  
|<span data-ttu-id="d112a-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="d112a-142">Element</span></span>|<span data-ttu-id="d112a-143">Popis</span><span class="sxs-lookup"><span data-stu-id="d112a-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d112a-144">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d112a-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d112a-145">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="d112a-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d112a-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="d112a-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="d112a-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d112a-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
