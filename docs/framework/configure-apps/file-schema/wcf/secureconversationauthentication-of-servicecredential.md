---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 13e9312e4c4eade003fec77909a743009aa9bca7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278522"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="da1f4-102">\<secureConversationAuthentication> of \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="da1f4-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="da1f4-103">Určuje nastavení pro služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="da1f4-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="da1f4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="da1f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="da1f4-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="da1f4-105">\<behaviors></span></span>  
<span data-ttu-id="da1f4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="da1f4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="da1f4-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="da1f4-107">\<behavior></span></span>  
<span data-ttu-id="da1f4-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="da1f4-108">\<serviceCredentials></span></span>  
<span data-ttu-id="da1f4-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="da1f4-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1f4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da1f4-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da1f4-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da1f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="da1f4-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da1f4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da1f4-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="da1f4-113">Attributes</span></span>  
  
|<span data-ttu-id="da1f4-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="da1f4-114">Attribute</span></span>|<span data-ttu-id="da1f4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f4-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="da1f4-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> má být použit.</span><span class="sxs-lookup"><span data-stu-id="da1f4-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da1f4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="da1f4-117">Child Elements</span></span>  
 <span data-ttu-id="da1f4-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="da1f4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da1f4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="da1f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="da1f4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="da1f4-120">Element</span></span>|<span data-ttu-id="da1f4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da1f4-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="da1f4-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="da1f4-123">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="da1f4-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da1f4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da1f4-124">Remarks</span></span>  
 <span data-ttu-id="da1f4-125">Použijte tento prvek konfigurace pro zadání seznamu známé deklarace typů pro serializaci soubory cookie zabezpečení kontextu Token (SCT), stejně jako kodéru pro kódování a zabezpečit informace soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="da1f4-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="da1f4-126">Další informace o SCT najdete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="da1f4-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1f4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da1f4-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
