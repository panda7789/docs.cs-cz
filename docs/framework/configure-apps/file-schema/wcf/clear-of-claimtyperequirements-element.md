---
title: <clear><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400531"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="ab839-102">\<clear>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="ab839-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="ab839-103">Určuje, že všechny typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="ab839-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="ab839-104">Tím se zajistí, že kolekce začne být prázdná.</span><span class="sxs-lookup"><span data-stu-id="ab839-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="ab839-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab839-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab839-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab839-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ab839-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab839-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab839-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab839-108">Attributes</span></span>  
 <span data-ttu-id="ab839-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab839-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab839-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab839-110">Child Elements</span></span>  
 <span data-ttu-id="ab839-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab839-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab839-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab839-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ab839-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab839-113">Element</span></span>|<span data-ttu-id="ab839-114">Description</span><span class="sxs-lookup"><span data-stu-id="ab839-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="ab839-115">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="ab839-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="ab839-116">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="ab839-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="ab839-117">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="ab839-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ab839-118">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="ab839-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ab839-119">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="ab839-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab839-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab839-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
