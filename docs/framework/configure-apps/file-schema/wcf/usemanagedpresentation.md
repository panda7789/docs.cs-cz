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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f99879ab80acddf1d50f5e5c734b8d6c975cb348
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="04103-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="04103-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="04103-103">Vazba element, který používá ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="04103-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="04103-104">Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="04103-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="04103-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="04103-105">\<system.serviceModel></span></span>  
<span data-ttu-id="04103-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="04103-106">\<bindings></span></span>  
<span data-ttu-id="04103-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="04103-107">\<customBinding></span></span>  
<span data-ttu-id="04103-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="04103-108">\<binding></span></span>  
<span data-ttu-id="04103-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="04103-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04103-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04103-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04103-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04103-111">Attributes and Elements</span></span>  
 <span data-ttu-id="04103-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04103-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04103-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="04103-113">Attributes</span></span>  
 <span data-ttu-id="04103-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="04103-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04103-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04103-115">Child Elements</span></span>  
 <span data-ttu-id="04103-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="04103-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04103-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04103-117">Parent Elements</span></span>  
  
|<span data-ttu-id="04103-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="04103-118">Element</span></span>|<span data-ttu-id="04103-119">Popis</span><span class="sxs-lookup"><span data-stu-id="04103-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04103-120">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="04103-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="04103-121">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="04103-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04103-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04103-122">Remarks</span></span>  
 <span data-ttu-id="04103-123">Tento element se používá pomocí zprostředkovatele identity pro vyjádření v svých zásad fakt, že podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="04103-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="04103-124">Zprostředkovatelů identity, které publikují takové výraz zásad byste měli mít problém tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="04103-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04103-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="04103-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="04103-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="04103-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="04103-127">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="04103-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="04103-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="04103-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="04103-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="04103-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
