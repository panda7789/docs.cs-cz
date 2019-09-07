---
title: <remove><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399988"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="b47c9-102">\<odebrat > \<elementu > claimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="b47c9-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="b47c9-103">Určuje typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="b47c9-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="b47c9-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b47c9-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b47c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b47c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b47c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="b47c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b47c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b47c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b47c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="b47c9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="b47c9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="b47c9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47c9-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b47c9-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b47c9-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b47c9-114">Attributes and Elements</span></span>  
 <span data-ttu-id="b47c9-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b47c9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b47c9-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="b47c9-116">Attributes</span></span>  
  
|<span data-ttu-id="b47c9-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="b47c9-117">Attribute</span></span>|<span data-ttu-id="b47c9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b47c9-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b47c9-119">claimType</span><span class="sxs-lookup"><span data-stu-id="b47c9-119">claimType</span></span>|<span data-ttu-id="b47c9-120">Identifikátor URI definující typ deklarace, který má být odebrán.</span><span class="sxs-lookup"><span data-stu-id="b47c9-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b47c9-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b47c9-121">Child Elements</span></span>  
 <span data-ttu-id="b47c9-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="b47c9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b47c9-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b47c9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b47c9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b47c9-124">Element</span></span>|<span data-ttu-id="b47c9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b47c9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b47c9-126">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b47c9-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="b47c9-127">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="b47c9-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b47c9-128">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="b47c9-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b47c9-129">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="b47c9-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b47c9-130">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="b47c9-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b47c9-131">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="b47c9-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b47c9-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b47c9-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
