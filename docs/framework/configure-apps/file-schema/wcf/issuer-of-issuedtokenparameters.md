---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397934"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="dcdb1-102">\<issuer> z \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="dcdb1-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="dcdb1-103">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="dcdb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdb1-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcdb1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dcdb1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dcdb1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcdb1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="dcdb1-107">Attributes</span></span>  
  
|<span data-ttu-id="dcdb1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="dcdb1-108">Attribute</span></span>|<span data-ttu-id="dcdb1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dcdb1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcdb1-110">adresa</span><span class="sxs-lookup"><span data-stu-id="dcdb1-110">address</span></span>|<span data-ttu-id="dcdb1-111">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-111">Required string.</span></span> <span data-ttu-id="dcdb1-112">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="dcdb1-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcdb1-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dcdb1-113">Child Elements</span></span>  
  
|<span data-ttu-id="dcdb1-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcdb1-114">Element</span></span>|<span data-ttu-id="dcdb1-115">Description</span><span class="sxs-lookup"><span data-stu-id="dcdb1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="dcdb1-116">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="dcdb1-117">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcdb1-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dcdb1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dcdb1-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcdb1-119">Element</span></span>|<span data-ttu-id="dcdb1-120">Description</span><span class="sxs-lookup"><span data-stu-id="dcdb1-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="dcdb1-121">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="dcdb1-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcdb1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcdb1-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="dcdb1-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="dcdb1-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="dcdb1-124">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="dcdb1-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dcdb1-125">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="dcdb1-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="dcdb1-126">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="dcdb1-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dcdb1-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="dcdb1-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dcdb1-128">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="dcdb1-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dcdb1-129">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="dcdb1-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="dcdb1-130">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="dcdb1-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="dcdb1-131">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="dcdb1-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
