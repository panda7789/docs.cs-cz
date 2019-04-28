---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698457"
---
# <a name="xmlelement"></a><span data-ttu-id="12244-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="12244-101">\<xmlElement></span></span>
<span data-ttu-id="12244-102">Určuje element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="12244-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="12244-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12244-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="12244-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="12244-104">\<bindings></span></span>  
<span data-ttu-id="12244-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="12244-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="12244-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="12244-106">\<binding></span></span>  
<span data-ttu-id="12244-107">\<security></span><span class="sxs-lookup"><span data-stu-id="12244-107">\<security></span></span>  
<span data-ttu-id="12244-108">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="12244-108">\<message></span></span>  
<span data-ttu-id="12244-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="12244-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12244-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12244-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12244-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12244-111">Attributes and Elements</span></span>  
 <span data-ttu-id="12244-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12244-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12244-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="12244-113">Attributes</span></span>  
  
|<span data-ttu-id="12244-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="12244-114">Attribute</span></span>|<span data-ttu-id="12244-115">Popis</span><span class="sxs-lookup"><span data-stu-id="12244-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12244-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="12244-116">xmlElement</span></span>|<span data-ttu-id="12244-117">Řetězec určující element XML, který posílá v těle zprávy služby tokenů zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="12244-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12244-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12244-118">Child Elements</span></span>  
 <span data-ttu-id="12244-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="12244-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12244-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12244-120">Parent Elements</span></span>  
  
|<span data-ttu-id="12244-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="12244-121">Element</span></span>|<span data-ttu-id="12244-122">Popis</span><span class="sxs-lookup"><span data-stu-id="12244-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12244-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="12244-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="12244-124">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="12244-124">A collection of token request parameters.</span></span> <span data-ttu-id="12244-125">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="12244-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12244-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12244-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="12244-127">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="12244-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="12244-128">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="12244-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="12244-129">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="12244-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="12244-130">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="12244-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="12244-131">Vazby</span><span class="sxs-lookup"><span data-stu-id="12244-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
