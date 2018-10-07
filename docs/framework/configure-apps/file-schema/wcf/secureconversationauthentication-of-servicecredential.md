---
title: '&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
ms.openlocfilehash: 3adcf7ba9814bcf494d345cf0e3f47c57df2152c
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841745"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="ac66c-102">&lt;secureConversationAuthentication&gt; – &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ac66c-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="ac66c-103">Určuje nastavení pro služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="ac66c-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="ac66c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ac66c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ac66c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ac66c-105">\<behaviors></span></span>  
<span data-ttu-id="ac66c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ac66c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ac66c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ac66c-107">\<behavior></span></span>  
<span data-ttu-id="ac66c-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ac66c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ac66c-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ac66c-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac66c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac66c-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac66c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ac66c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ac66c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ac66c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac66c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ac66c-113">Attributes</span></span>  
  
|<span data-ttu-id="ac66c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="ac66c-114">Attribute</span></span>|<span data-ttu-id="ac66c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ac66c-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="ac66c-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="ac66c-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac66c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ac66c-117">Child Elements</span></span>  
 <span data-ttu-id="ac66c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac66c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac66c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ac66c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ac66c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ac66c-120">Element</span></span>|<span data-ttu-id="ac66c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ac66c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac66c-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ac66c-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="ac66c-123">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="ac66c-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac66c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac66c-124">Remarks</span></span>  
 <span data-ttu-id="ac66c-125">Použijte tento prvek konfigurace pro zadání seznamu známé deklarace typů pro serializaci soubory cookie zabezpečení kontextu Token (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="ac66c-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="ac66c-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="ac66c-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac66c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac66c-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
