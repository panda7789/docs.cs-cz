---
title: '&lt;xmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 40703bdf62e8c69ac7e09a0d715e2a2f99408680
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612278"
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="f3cd7-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="f3cd7-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="f3cd7-103">Určuje element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f3cd7-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="f3cd7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3cd7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3cd7-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f3cd7-105">\<bindings></span></span>  
<span data-ttu-id="f3cd7-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="f3cd7-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="f3cd7-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f3cd7-107">\<binding></span></span>  
<span data-ttu-id="f3cd7-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f3cd7-108">\<security></span></span>  
<span data-ttu-id="f3cd7-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="f3cd7-109">\<message></span></span>  
<span data-ttu-id="f3cd7-110">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="f3cd7-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3cd7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3cd7-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3cd7-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3cd7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f3cd7-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3cd7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3cd7-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3cd7-114">Attributes</span></span>  
  
|<span data-ttu-id="f3cd7-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3cd7-115">Attribute</span></span>|<span data-ttu-id="f3cd7-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f3cd7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3cd7-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="f3cd7-117">xmlElement</span></span>|<span data-ttu-id="f3cd7-118">Řetězec určující element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f3cd7-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3cd7-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3cd7-119">Child Elements</span></span>  
 <span data-ttu-id="f3cd7-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3cd7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3cd7-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3cd7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3cd7-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3cd7-122">Element</span></span>|<span data-ttu-id="f3cd7-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f3cd7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3cd7-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="f3cd7-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="f3cd7-125">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="f3cd7-125">A collection of token request parameters.</span></span> <span data-ttu-id="f3cd7-126">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="f3cd7-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3cd7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3cd7-127">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="f3cd7-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="f3cd7-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f3cd7-129">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f3cd7-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f3cd7-130">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="f3cd7-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="f3cd7-131">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f3cd7-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f3cd7-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="f3cd7-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
