---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398988"
---
# \<xmlElement>
<span data-ttu-id="90042-101">Určuje element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="90042-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="90042-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90042-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90042-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90042-103">Attributes and Elements</span></span>  
 <span data-ttu-id="90042-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90042-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90042-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="90042-105">Attributes</span></span>  
  
|<span data-ttu-id="90042-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="90042-106">Attribute</span></span>|<span data-ttu-id="90042-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90042-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90042-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="90042-108">xmlElement</span></span>|<span data-ttu-id="90042-109">Řetězec určující element XML, který je odeslán v těle zprávy do služby tokenu zabezpečení při vyžádání tokenu.</span><span class="sxs-lookup"><span data-stu-id="90042-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90042-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90042-110">Child Elements</span></span>  
 <span data-ttu-id="90042-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="90042-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90042-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90042-112">Parent Elements</span></span>  
  
|<span data-ttu-id="90042-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="90042-113">Element</span></span>|<span data-ttu-id="90042-114">Description</span><span class="sxs-lookup"><span data-stu-id="90042-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="90042-115">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="90042-115">A collection of token request parameters.</span></span> <span data-ttu-id="90042-116">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="90042-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90042-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="90042-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="90042-118">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="90042-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="90042-119">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="90042-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="90042-120">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="90042-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="90042-121">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="90042-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="90042-122">Vazby</span><span class="sxs-lookup"><span data-stu-id="90042-122">Bindings</span></span>](../../../wcf/bindings.md)
