---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400343"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="9388d-102">\<issuerMetadata> z \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="9388d-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="9388d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9388d-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9388d-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9388d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9388d-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9388d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9388d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="9388d-106">Attributes</span></span>  
  
|<span data-ttu-id="9388d-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="9388d-107">Attribute</span></span>|<span data-ttu-id="9388d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9388d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9388d-109">adresa</span><span class="sxs-lookup"><span data-stu-id="9388d-109">address</span></span>|<span data-ttu-id="9388d-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9388d-110">Required.</span></span> <span data-ttu-id="9388d-111">Řetězec, který určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9388d-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="9388d-112">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="9388d-112">The address must be an absolute URI.</span></span> <span data-ttu-id="9388d-113">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9388d-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9388d-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9388d-114">Child Elements</span></span>  
  
|<span data-ttu-id="9388d-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="9388d-115">Element</span></span>|<span data-ttu-id="9388d-116">Description</span><span class="sxs-lookup"><span data-stu-id="9388d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="9388d-117">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="9388d-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="9388d-118">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="9388d-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9388d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9388d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9388d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9388d-120">Element</span></span>|<span data-ttu-id="9388d-121">Description</span><span class="sxs-lookup"><span data-stu-id="9388d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="9388d-122">Určuje parametry tokenu zabezpečení vydaného ve federovaném scénáři zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9388d-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9388d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9388d-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9388d-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="9388d-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9388d-125">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="9388d-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9388d-126">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="9388d-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9388d-127">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="9388d-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9388d-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="9388d-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9388d-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="9388d-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9388d-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9388d-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="9388d-131">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9388d-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="9388d-132">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="9388d-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
