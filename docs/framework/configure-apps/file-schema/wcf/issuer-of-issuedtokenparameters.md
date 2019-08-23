---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 77ed9534ce872e805a6a6ea2c21a38710e6bc0fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925269"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="b6184-102">\<Vystavitel > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b6184-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="b6184-103">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b6184-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="b6184-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b6184-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b6184-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="b6184-105">\<bindings></span></span>  
<span data-ttu-id="b6184-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b6184-106">\<customBinding></span></span>  
<span data-ttu-id="b6184-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="b6184-107">\<binding></span></span>  
<span data-ttu-id="b6184-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b6184-108">\<security></span></span>  
<span data-ttu-id="b6184-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b6184-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b6184-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="b6184-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6184-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6184-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6184-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6184-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b6184-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6184-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6184-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6184-114">Attributes</span></span>  
  
|<span data-ttu-id="b6184-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6184-115">Attribute</span></span>|<span data-ttu-id="b6184-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b6184-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6184-117">adresa</span><span class="sxs-lookup"><span data-stu-id="b6184-117">address</span></span>|<span data-ttu-id="b6184-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="b6184-118">Required string.</span></span> <span data-ttu-id="b6184-119">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="b6184-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6184-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6184-120">Child Elements</span></span>  
  
|<span data-ttu-id="b6184-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6184-121">Element</span></span>|<span data-ttu-id="b6184-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b6184-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6184-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="b6184-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="b6184-124">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b6184-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="b6184-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="b6184-125">\<identity></span></span>](identity.md)|<span data-ttu-id="b6184-126">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="b6184-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6184-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6184-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b6184-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6184-128">Element</span></span>|<span data-ttu-id="b6184-129">Popis</span><span class="sxs-lookup"><span data-stu-id="b6184-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6184-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="b6184-130">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="b6184-131">Určuje aktuální vydaný token.</span><span class="sxs-lookup"><span data-stu-id="b6184-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6184-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6184-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b6184-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="b6184-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b6184-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="b6184-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b6184-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="b6184-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b6184-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="b6184-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b6184-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="b6184-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6184-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b6184-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b6184-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b6184-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b6184-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b6184-140">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b6184-141">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b6184-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b6184-142">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="b6184-142">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
