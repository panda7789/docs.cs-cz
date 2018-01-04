---
title: "&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f80b0570055edbe15fa467ea83e11aba2b62a8fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="4af61-102">&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="4af61-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="4af61-103">Určuje nastavení pro službu zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="4af61-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="4af61-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4af61-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4af61-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4af61-105">\<behaviors></span></span>  
<span data-ttu-id="4af61-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4af61-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4af61-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4af61-107">\<behavior></span></span>  
<span data-ttu-id="4af61-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="4af61-108">\<serviceCredentials></span></span>  
<span data-ttu-id="4af61-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="4af61-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af61-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4af61-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4af61-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4af61-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4af61-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4af61-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4af61-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4af61-113">Attributes</span></span>  
  
|<span data-ttu-id="4af61-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="4af61-114">Attribute</span></span>|<span data-ttu-id="4af61-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4af61-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="4af61-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="4af61-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4af61-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4af61-117">Child Elements</span></span>  
 <span data-ttu-id="4af61-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4af61-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4af61-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4af61-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4af61-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4af61-120">Element</span></span>|<span data-ttu-id="4af61-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4af61-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4af61-122">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="4af61-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="4af61-123">Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="4af61-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4af61-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4af61-124">Remarks</span></span>  
 <span data-ttu-id="4af61-125">Tento prvek konfigurace slouží k určení seznam typů známé deklarace identity pro soubory cookie serializaci tokenu pro kontext zabezpečení (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="4af61-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="4af61-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="4af61-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af61-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4af61-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
