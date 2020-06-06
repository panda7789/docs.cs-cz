---
title: <remove><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399988"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="114ba-102">\<remove>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="114ba-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="114ba-103">Určuje typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="114ba-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="114ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="114ba-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="114ba-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="114ba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="114ba-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="114ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="114ba-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="114ba-107">Attributes</span></span>  
  
|<span data-ttu-id="114ba-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="114ba-108">Attribute</span></span>|<span data-ttu-id="114ba-109">Popis</span><span class="sxs-lookup"><span data-stu-id="114ba-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="114ba-110">claimType</span><span class="sxs-lookup"><span data-stu-id="114ba-110">claimType</span></span>|<span data-ttu-id="114ba-111">Identifikátor URI definující typ deklarace, který má být odebrán.</span><span class="sxs-lookup"><span data-stu-id="114ba-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="114ba-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="114ba-112">Child Elements</span></span>  
 <span data-ttu-id="114ba-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="114ba-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="114ba-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="114ba-114">Parent Elements</span></span>  
  
|<span data-ttu-id="114ba-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="114ba-115">Element</span></span>|<span data-ttu-id="114ba-116">Description</span><span class="sxs-lookup"><span data-stu-id="114ba-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="114ba-117">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="114ba-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="114ba-118">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="114ba-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="114ba-119">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="114ba-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="114ba-120">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="114ba-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="114ba-121">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="114ba-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="114ba-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="114ba-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
