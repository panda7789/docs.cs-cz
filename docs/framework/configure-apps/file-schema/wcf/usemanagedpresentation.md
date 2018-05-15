---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 35af7f5e10594617807384c20ab706ad675d11ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="da735-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="da735-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="da735-103">Vazba element, který používá ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="da735-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="da735-104">Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="da735-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="da735-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da735-105">\<system.serviceModel></span></span>  
<span data-ttu-id="da735-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="da735-106">\<bindings></span></span>  
<span data-ttu-id="da735-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="da735-107">\<customBinding></span></span>  
<span data-ttu-id="da735-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="da735-108">\<binding></span></span>  
<span data-ttu-id="da735-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="da735-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da735-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da735-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da735-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da735-111">Attributes and Elements</span></span>  
 <span data-ttu-id="da735-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da735-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da735-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="da735-113">Attributes</span></span>  
 <span data-ttu-id="da735-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="da735-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da735-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="da735-115">Child Elements</span></span>  
 <span data-ttu-id="da735-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="da735-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da735-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="da735-117">Parent Elements</span></span>  
  
|<span data-ttu-id="da735-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="da735-118">Element</span></span>|<span data-ttu-id="da735-119">Popis</span><span class="sxs-lookup"><span data-stu-id="da735-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da735-120">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="da735-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="da735-121">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="da735-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da735-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da735-122">Remarks</span></span>  
 <span data-ttu-id="da735-123">Tento element se používá pomocí zprostředkovatele identity pro vyjádření v svých zásad fakt, že podporuje CardSpace profilu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="da735-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="da735-124">Zprostředkovatelů identity, které publikují takové výraz zásad byste měli mít problém tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="da735-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da735-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="da735-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="da735-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="da735-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="da735-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="da735-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="da735-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="da735-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="da735-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="da735-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
