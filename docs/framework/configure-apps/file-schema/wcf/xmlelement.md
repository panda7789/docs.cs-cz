---
title: '&lt;Třída XmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 6a197f7aa29645a08a581bcee103eb94c0e20179
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147015"
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="f5f2c-102">&lt;Třída XmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="f5f2c-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="f5f2c-103">Určuje element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f5f2c-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="f5f2c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5f2c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5f2c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-105">\<bindings></span></span>  
<span data-ttu-id="f5f2c-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="f5f2c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-107">\<binding></span></span>  
<span data-ttu-id="f5f2c-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-108">\<security></span></span>  
<span data-ttu-id="f5f2c-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-109">\<message></span></span>  
<span data-ttu-id="f5f2c-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="f5f2c-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f2c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5f2c-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5f2c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f5f2c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f5f2c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f5f2c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5f2c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f5f2c-114">Attributes</span></span>  
  
|<span data-ttu-id="f5f2c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f5f2c-115">Attribute</span></span>|<span data-ttu-id="f5f2c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f5f2c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5f2c-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="f5f2c-117">xmlElement</span></span>|<span data-ttu-id="f5f2c-118">Řetězec určující element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="f5f2c-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5f2c-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f5f2c-119">Child Elements</span></span>  
 <span data-ttu-id="f5f2c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="f5f2c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5f2c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f5f2c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f5f2c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="f5f2c-122">Element</span></span>|<span data-ttu-id="f5f2c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f5f2c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5f2c-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="f5f2c-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="f5f2c-125">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="f5f2c-125">A collection of token request parameters.</span></span> <span data-ttu-id="f5f2c-126">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="f5f2c-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5f2c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5f2c-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="f5f2c-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="f5f2c-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f5f2c-129">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f5f2c-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f5f2c-130">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="f5f2c-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="f5f2c-131">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f5f2c-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f5f2c-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="f5f2c-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
