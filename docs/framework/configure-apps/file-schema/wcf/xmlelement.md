---
title: '&lt;xmlElement.&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1efe32121bc5744c305ff8ef8eefabd8a9d19e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="a22f4-102">&lt;xmlElement.&gt;</span><span class="sxs-lookup"><span data-stu-id="a22f4-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="a22f4-103">Určuje element XML, který je odeslána v textu zprávy do služby tokenů zabezpečení Pokud požadování tokenu.</span><span class="sxs-lookup"><span data-stu-id="a22f4-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="a22f4-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a22f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a22f4-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a22f4-105">\<bindings></span></span>  
<span data-ttu-id="a22f4-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a22f4-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a22f4-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a22f4-107">\<binding></span></span>  
<span data-ttu-id="a22f4-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a22f4-108">\<security></span></span>  
<span data-ttu-id="a22f4-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="a22f4-109">\<message></span></span>  
<span data-ttu-id="a22f4-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a22f4-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22f4-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a22f4-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a22f4-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a22f4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a22f4-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a22f4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a22f4-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="a22f4-114">Attributes</span></span>  
  
|<span data-ttu-id="a22f4-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="a22f4-115">Attribute</span></span>|<span data-ttu-id="a22f4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a22f4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a22f4-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a22f4-117">xmlElement</span></span>|<span data-ttu-id="a22f4-118">Řetězec určující element XML, který je odeslána v textu zprávy do služby tokenů zabezpečení Pokud požadování tokenu.</span><span class="sxs-lookup"><span data-stu-id="a22f4-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a22f4-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a22f4-119">Child Elements</span></span>  
 <span data-ttu-id="a22f4-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="a22f4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a22f4-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a22f4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a22f4-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="a22f4-122">Element</span></span>|<span data-ttu-id="a22f4-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a22f4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a22f4-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a22f4-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="a22f4-125">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="a22f4-125">A collection of token request parameters.</span></span> <span data-ttu-id="a22f4-126">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="a22f4-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a22f4-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a22f4-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="a22f4-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a22f4-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a22f4-129">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a22f4-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a22f4-130">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="a22f4-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a22f4-131">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a22f4-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a22f4-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="a22f4-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
