---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397934"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="5a3a3-102">\<Vystavitel > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="5a3a3-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="5a3a3-103">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="5a3a3-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a3a3-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a3a3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5a3a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5a3a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="5a3a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5a3a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="5a3a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="5a3a3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="5a3a3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vystavitele**</span><span class="sxs-lookup"><span data-stu-id="5a3a3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3a3-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a3a3-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a3a3-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a3a3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5a3a3-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a3a3-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a3a3-115">Attributes</span></span>  
  
|<span data-ttu-id="5a3a3-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a3a3-116">Attribute</span></span>|<span data-ttu-id="5a3a3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5a3a3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a3a3-118">adresa</span><span class="sxs-lookup"><span data-stu-id="5a3a3-118">address</span></span>|<span data-ttu-id="5a3a3-119">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-119">Required string.</span></span> <span data-ttu-id="5a3a3-120">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="5a3a3-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a3a3-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a3a3-121">Child Elements</span></span>  
  
|<span data-ttu-id="5a3a3-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a3a3-122">Element</span></span>|<span data-ttu-id="5a3a3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5a3a3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3a3-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="5a3a3-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="5a3a3-125">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="5a3a3-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="5a3a3-126">\<identity></span></span>](identity.md)|<span data-ttu-id="5a3a3-127">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a3a3-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a3a3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5a3a3-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a3a3-129">Element</span></span>|<span data-ttu-id="5a3a3-130">Popis</span><span class="sxs-lookup"><span data-stu-id="5a3a3-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3a3-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="5a3a3-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="5a3a3-132">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="5a3a3-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a3a3-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a3a3-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5a3a3-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="5a3a3-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5a3a3-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5a3a3-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5a3a3-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="5a3a3-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5a3a3-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5a3a3-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5a3a3-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="5a3a3-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5a3a3-139">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5a3a3-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5a3a3-140">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5a3a3-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5a3a3-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5a3a3-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="5a3a3-142">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5a3a3-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="5a3a3-143">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="5a3a3-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
