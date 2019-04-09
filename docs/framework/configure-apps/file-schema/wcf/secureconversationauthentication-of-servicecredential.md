---
title: <secureConversationAuthentication> of <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: f35392b91d047c46e65ce433ef544b86cf6c88c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083696"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="28ff8-102">\<secureConversationAuthentication> of \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="28ff8-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="28ff8-103">Určuje nastavení pro služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="28ff8-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="28ff8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28ff8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28ff8-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28ff8-105">\<behaviors></span></span>  
<span data-ttu-id="28ff8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="28ff8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="28ff8-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28ff8-107">\<behavior></span></span>  
<span data-ttu-id="28ff8-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="28ff8-108">\<serviceCredentials></span></span>  
<span data-ttu-id="28ff8-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="28ff8-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ff8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28ff8-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28ff8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28ff8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28ff8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28ff8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28ff8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="28ff8-113">Attributes</span></span>  
  
|<span data-ttu-id="28ff8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="28ff8-114">Attribute</span></span>|<span data-ttu-id="28ff8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="28ff8-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="28ff8-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="28ff8-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28ff8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28ff8-117">Child Elements</span></span>  
 <span data-ttu-id="28ff8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="28ff8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28ff8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28ff8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="28ff8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="28ff8-120">Element</span></span>|<span data-ttu-id="28ff8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="28ff8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28ff8-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="28ff8-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="28ff8-123">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="28ff8-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ff8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28ff8-124">Remarks</span></span>  
 <span data-ttu-id="28ff8-125">Použijte tento prvek konfigurace pro zadání seznamu známé deklarace typů pro serializaci soubory cookie zabezpečení kontextu Token (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="28ff8-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="28ff8-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="28ff8-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ff8-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28ff8-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
