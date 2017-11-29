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
ms.openlocfilehash: 0fb9ff476812b6b889750e8eb7b80efce801f041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="ae30a-102">&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ae30a-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="ae30a-103">Určuje nastavení pro službu zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="ae30a-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="ae30a-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ae30a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae30a-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ae30a-105">\<behaviors></span></span>  
<span data-ttu-id="ae30a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ae30a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ae30a-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ae30a-107">\<behavior></span></span>  
<span data-ttu-id="ae30a-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ae30a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ae30a-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ae30a-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae30a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae30a-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae30a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae30a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ae30a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae30a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae30a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae30a-113">Attributes</span></span>  
  
|<span data-ttu-id="ae30a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae30a-114">Attribute</span></span>|<span data-ttu-id="ae30a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ae30a-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="ae30a-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="ae30a-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae30a-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae30a-117">Child Elements</span></span>  
 <span data-ttu-id="ae30a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae30a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae30a-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae30a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ae30a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae30a-120">Element</span></span>|<span data-ttu-id="ae30a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ae30a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae30a-122">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ae30a-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="ae30a-123">Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="ae30a-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae30a-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae30a-124">Remarks</span></span>  
 <span data-ttu-id="ae30a-125">Tento prvek konfigurace slouží k určení seznam typů známé deklarace identity pro soubory cookie serializaci tokenu pro kontext zabezpečení (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="ae30a-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="ae30a-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="ae30a-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae30a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae30a-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
