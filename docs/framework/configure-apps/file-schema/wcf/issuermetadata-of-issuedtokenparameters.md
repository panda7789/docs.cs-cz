---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400343"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="5ab06-102">\<issuerMetadata > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="5ab06-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="5ab06-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ab06-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ab06-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5ab06-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5ab06-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="5ab06-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5ab06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="5ab06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="5ab06-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="5ab06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="5ab06-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab06-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ab06-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ab06-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ab06-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ab06-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ab06-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ab06-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ab06-114">Attributes</span></span>  
  
|<span data-ttu-id="5ab06-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ab06-115">Attribute</span></span>|<span data-ttu-id="5ab06-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5ab06-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ab06-117">adresa</span><span class="sxs-lookup"><span data-stu-id="5ab06-117">address</span></span>|<span data-ttu-id="5ab06-118">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5ab06-118">Required.</span></span> <span data-ttu-id="5ab06-119">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5ab06-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="5ab06-120">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="5ab06-120">The address must be an absolute URI.</span></span> <span data-ttu-id="5ab06-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5ab06-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ab06-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ab06-122">Child Elements</span></span>  
  
|<span data-ttu-id="5ab06-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ab06-123">Element</span></span>|<span data-ttu-id="5ab06-124">Popis</span><span class="sxs-lookup"><span data-stu-id="5ab06-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab06-125">\<headers></span><span class="sxs-lookup"><span data-stu-id="5ab06-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="5ab06-126">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="5ab06-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="5ab06-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="5ab06-127">\<identity></span></span>](identity.md)|<span data-ttu-id="5ab06-128">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ab06-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ab06-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ab06-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5ab06-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ab06-130">Element</span></span>|<span data-ttu-id="5ab06-131">Popis</span><span class="sxs-lookup"><span data-stu-id="5ab06-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab06-132">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="5ab06-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="5ab06-133">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5ab06-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ab06-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ab06-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5ab06-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="5ab06-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5ab06-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5ab06-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5ab06-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="5ab06-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5ab06-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5ab06-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5ab06-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="5ab06-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ab06-140">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5ab06-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5ab06-141">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5ab06-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5ab06-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5ab06-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="5ab06-143">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5ab06-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="5ab06-144">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="5ab06-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
