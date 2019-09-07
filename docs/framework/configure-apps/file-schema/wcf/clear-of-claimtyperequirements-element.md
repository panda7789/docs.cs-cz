---
title: <clear><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400531"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="d3326-102">\<Vymazat > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d3326-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d3326-103">Určuje, že všechny typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="d3326-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="d3326-104">Tím se zajistí, že kolekce začne být prázdná.</span><span class="sxs-lookup"><span data-stu-id="d3326-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="d3326-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3326-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d3326-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d3326-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d3326-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="d3326-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d3326-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d3326-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d3326-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="d3326-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="d3326-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="d3326-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3326-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3326-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3326-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3326-115">Attributes and Elements</span></span>  
 <span data-ttu-id="d3326-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3326-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3326-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3326-117">Attributes</span></span>  
 <span data-ttu-id="d3326-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3326-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3326-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3326-119">Child Elements</span></span>  
 <span data-ttu-id="d3326-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3326-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3326-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3326-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3326-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3326-122">Element</span></span>|<span data-ttu-id="d3326-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d3326-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3326-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d3326-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="d3326-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d3326-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d3326-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d3326-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d3326-127">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d3326-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d3326-128">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d3326-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d3326-129">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="d3326-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3326-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3326-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
