---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398988"
---
# <a name="xmlelement"></a><span data-ttu-id="61dc9-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="61dc9-101">\<xmlElement></span></span>
<span data-ttu-id="61dc9-102">Určuje element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="61dc9-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="61dc9-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61dc9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="61dc9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="61dc9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61dc9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="61dc9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="61dc9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61dc9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61dc9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tokenRequestParameters >** ](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="61dc9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="61dc9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> xmlElement**</span><span class="sxs-lookup"><span data-stu-id="61dc9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61dc9-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61dc9-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61dc9-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61dc9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="61dc9-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61dc9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61dc9-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="61dc9-115">Attributes</span></span>  
  
|<span data-ttu-id="61dc9-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="61dc9-116">Attribute</span></span>|<span data-ttu-id="61dc9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="61dc9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61dc9-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="61dc9-118">xmlElement</span></span>|<span data-ttu-id="61dc9-119">Řetězec určující element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="61dc9-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61dc9-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61dc9-120">Child Elements</span></span>  
 <span data-ttu-id="61dc9-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="61dc9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61dc9-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61dc9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="61dc9-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="61dc9-123">Element</span></span>|<span data-ttu-id="61dc9-124">Popis</span><span class="sxs-lookup"><span data-stu-id="61dc9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61dc9-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="61dc9-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="61dc9-126">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="61dc9-126">A collection of token request parameters.</span></span> <span data-ttu-id="61dc9-127">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="61dc9-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61dc9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61dc9-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="61dc9-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="61dc9-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="61dc9-130">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="61dc9-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="61dc9-131">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="61dc9-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="61dc9-132">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="61dc9-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="61dc9-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="61dc9-133">Bindings</span></span>](../../../wcf/bindings.md)
