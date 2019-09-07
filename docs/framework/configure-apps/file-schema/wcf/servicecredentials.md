---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399658"
---
# <a name="servicecredentials"></a><span data-ttu-id="bb046-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bb046-101">\<serviceCredentials></span></span>
<span data-ttu-id="bb046-102">Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="bb046-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
<span data-ttu-id="bb046-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb046-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb046-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bb046-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bb046-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bb046-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bb046-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bb046-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bb046-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bb046-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bb046-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**</span><span class="sxs-lookup"><span data-stu-id="bb046-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb046-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb046-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb046-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb046-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb046-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb046-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb046-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb046-112">Attributes</span></span>  
  
|<span data-ttu-id="bb046-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bb046-113">Attribute</span></span>|<span data-ttu-id="bb046-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bb046-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="bb046-115">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="bb046-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb046-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb046-116">Child Elements</span></span>  
  
|<span data-ttu-id="bb046-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb046-117">Element</span></span>|<span data-ttu-id="bb046-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bb046-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb046-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="bb046-119">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="bb046-120">Určuje certifikát, který má být použit v případě, že je klientský certifikát k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="bb046-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="bb046-121">Tento prvek také určuje nastavení ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="bb046-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="bb046-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="bb046-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="bb046-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="bb046-124">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="bb046-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="bb046-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="bb046-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="bb046-126">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="bb046-127">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="bb046-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="bb046-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="bb046-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="bb046-129">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="bb046-130">Určuje aktuální pověření pro zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="bb046-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="bb046-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="bb046-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="bb046-132">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="bb046-133">Určuje certifikát používaný službou k identifikaci sebe sama.</span><span class="sxs-lookup"><span data-stu-id="bb046-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="bb046-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="bb046-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="bb046-135">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="bb046-136">Určuje nastavení pro ověřování hesla uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="bb046-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="bb046-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="bb046-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="bb046-138">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="bb046-139">Určuje nastavení pro ověření přihlašovacích údajů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bb046-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="bb046-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bb046-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb046-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb046-141">Parent Elements</span></span>  
  
|<span data-ttu-id="bb046-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb046-142">Element</span></span>|<span data-ttu-id="bb046-143">Popis</span><span class="sxs-lookup"><span data-stu-id="bb046-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb046-144">\<> chování</span><span class="sxs-lookup"><span data-stu-id="bb046-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bb046-145">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="bb046-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb046-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb046-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="bb046-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb046-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
