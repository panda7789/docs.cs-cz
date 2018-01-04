---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="8c875-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="8c875-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="8c875-103">Vazba element, který používá ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="8c875-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8c875-104">Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="8c875-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="8c875-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8c875-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8c875-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8c875-106">\<bindings></span></span>  
<span data-ttu-id="8c875-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c875-107">\<customBinding></span></span>  
<span data-ttu-id="8c875-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="8c875-108">\<binding></span></span>  
<span data-ttu-id="8c875-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="8c875-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c875-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c875-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c875-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c875-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8c875-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c875-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c875-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c875-113">Attributes</span></span>  
 <span data-ttu-id="8c875-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c875-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c875-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c875-115">Child Elements</span></span>  
 <span data-ttu-id="8c875-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c875-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c875-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c875-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8c875-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c875-118">Element</span></span>|<span data-ttu-id="8c875-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8c875-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c875-120">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="8c875-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8c875-121">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="8c875-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c875-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c875-122">Remarks</span></span>  
 <span data-ttu-id="8c875-123">Tento element se používá pomocí zprostředkovatele identity pro vyjádření v svých zásad fakt, že podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="8c875-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8c875-124">Zprostředkovatelů identity, které publikují takové výraz zásad byste měli mít problém tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="8c875-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c875-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c875-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8c875-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="8c875-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8c875-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="8c875-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8c875-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="8c875-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8c875-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c875-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
