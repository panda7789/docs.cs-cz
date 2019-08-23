---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941441"
---
# <a name="xmlelement"></a><span data-ttu-id="3dab8-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="3dab8-101">\<xmlElement></span></span>
<span data-ttu-id="3dab8-102">Určuje element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="3dab8-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="3dab8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3dab8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3dab8-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3dab8-104">\<bindings></span></span>  
<span data-ttu-id="3dab8-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="3dab8-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3dab8-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3dab8-106">\<binding></span></span>  
<span data-ttu-id="3dab8-107">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3dab8-107">\<security></span></span>  
<span data-ttu-id="3dab8-108">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="3dab8-108">\<message></span></span>  
<span data-ttu-id="3dab8-109">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="3dab8-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dab8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dab8-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dab8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3dab8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3dab8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3dab8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dab8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3dab8-113">Attributes</span></span>  
  
|<span data-ttu-id="3dab8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3dab8-114">Attribute</span></span>|<span data-ttu-id="3dab8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3dab8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3dab8-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="3dab8-116">xmlElement</span></span>|<span data-ttu-id="3dab8-117">Řetězec určující element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="3dab8-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dab8-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3dab8-118">Child Elements</span></span>  
 <span data-ttu-id="3dab8-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="3dab8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3dab8-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3dab8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3dab8-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="3dab8-121">Element</span></span>|<span data-ttu-id="3dab8-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3dab8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dab8-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="3dab8-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="3dab8-124">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="3dab8-124">A collection of token request parameters.</span></span> <span data-ttu-id="3dab8-125">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="3dab8-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3dab8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dab8-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="3dab8-127">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="3dab8-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3dab8-128">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3dab8-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3dab8-129">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="3dab8-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3dab8-130">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3dab8-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3dab8-131">Vazby</span><span class="sxs-lookup"><span data-stu-id="3dab8-131">Bindings</span></span>](../../../wcf/bindings.md)
