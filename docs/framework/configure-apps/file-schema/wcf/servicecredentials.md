---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399658"
---
# \<serviceCredentials>
<span data-ttu-id="584ac-101">Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="584ac-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="584ac-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="584ac-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="584ac-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="584ac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="584ac-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="584ac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="584ac-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="584ac-105">Attributes</span></span>  
  
|<span data-ttu-id="584ac-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="584ac-106">Attribute</span></span>|<span data-ttu-id="584ac-107">Popis</span><span class="sxs-lookup"><span data-stu-id="584ac-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="584ac-108">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="584ac-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="584ac-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="584ac-109">Child Elements</span></span>  
  
|<span data-ttu-id="584ac-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="584ac-110">Element</span></span>|<span data-ttu-id="584ac-111">Description</span><span class="sxs-lookup"><span data-stu-id="584ac-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="584ac-112">Určuje certifikát, který má být použit v případě, že je klientský certifikát k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="584ac-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="584ac-113">Tento prvek také určuje nastavení ověřování klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="584ac-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="584ac-114">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="584ac-115">Určuje aktuální vydaný token pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="584ac-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="584ac-116">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="584ac-117">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="584ac-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="584ac-118">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="584ac-119">Určuje aktuální pověření pro zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="584ac-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="584ac-120">Tento prvek je typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="584ac-121">Určuje certifikát používaný službou k identifikaci sebe sama.</span><span class="sxs-lookup"><span data-stu-id="584ac-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="584ac-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="584ac-123">Určuje nastavení pro ověřování hesla uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="584ac-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="584ac-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="584ac-125">Určuje nastavení pro ověření přihlašovacích údajů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="584ac-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="584ac-126">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="584ac-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="584ac-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="584ac-127">Parent Elements</span></span>  
  
|<span data-ttu-id="584ac-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="584ac-128">Element</span></span>|<span data-ttu-id="584ac-129">Description</span><span class="sxs-lookup"><span data-stu-id="584ac-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="584ac-130">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="584ac-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="584ac-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="584ac-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="584ac-132">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="584ac-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
