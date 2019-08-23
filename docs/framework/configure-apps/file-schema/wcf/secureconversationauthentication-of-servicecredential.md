---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935834"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="9f0ee-102">\<secureConversationAuthentication > \<serviceCredential ></span><span class="sxs-lookup"><span data-stu-id="9f0ee-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="9f0ee-103">Určuje nastavení pro službu zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="9f0ee-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f0ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f0ee-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="9f0ee-105">\<behaviors></span></span>  
<span data-ttu-id="9f0ee-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f0ee-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f0ee-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="9f0ee-107">\<behavior></span></span>  
<span data-ttu-id="9f0ee-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9f0ee-108">\<serviceCredentials></span></span>  
<span data-ttu-id="9f0ee-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="9f0ee-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0ee-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f0ee-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f0ee-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f0ee-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f0ee-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f0ee-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f0ee-113">Attributes</span></span>  
  
|<span data-ttu-id="9f0ee-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f0ee-114">Attribute</span></span>|<span data-ttu-id="9f0ee-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9f0ee-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="9f0ee-116">Řetězec, který určuje typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , který se má použít.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f0ee-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f0ee-117">Child Elements</span></span>  
 <span data-ttu-id="9f0ee-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f0ee-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f0ee-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f0ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9f0ee-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f0ee-120">Element</span></span>|<span data-ttu-id="9f0ee-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9f0ee-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f0ee-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9f0ee-122">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="9f0ee-123">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f0ee-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f0ee-124">Remarks</span></span>  
 <span data-ttu-id="9f0ee-125">Tento prvek konfigurace slouží k určení seznamu známých typů deklarací pro serializaci souborů cookie tokenu zabezpečení (SCT) a také kodéru ke kódování a zabezpečení informací o souborech cookie.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="9f0ee-126">Další informace o SCT naleznete v tématu <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="9f0ee-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0ee-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f0ee-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
