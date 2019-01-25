---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 96490421addfadd9cef6b65bddaed0aae3370d15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720272"
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="184a1-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="184a1-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="184a1-103">Element vazby používaný ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profil WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="184a1-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="184a1-104">Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="184a1-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="184a1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="184a1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="184a1-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="184a1-106">\<bindings></span></span>  
<span data-ttu-id="184a1-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="184a1-107">\<customBinding></span></span>  
<span data-ttu-id="184a1-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="184a1-108">\<binding></span></span>  
<span data-ttu-id="184a1-109">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="184a1-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="184a1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="184a1-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="184a1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="184a1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="184a1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="184a1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="184a1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="184a1-113">Attributes</span></span>  
 <span data-ttu-id="184a1-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="184a1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="184a1-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="184a1-115">Child Elements</span></span>  
 <span data-ttu-id="184a1-116">Žádná</span><span class="sxs-lookup"><span data-stu-id="184a1-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="184a1-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="184a1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="184a1-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="184a1-118">Element</span></span>|<span data-ttu-id="184a1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="184a1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="184a1-120">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="184a1-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="184a1-121">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="184a1-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184a1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="184a1-122">Remarks</span></span>  
 <span data-ttu-id="184a1-123">Tento element se používá zprostředkovatel identity pro vyjádření v jeho zásad skutečnost, že podporuje CardSpace profil WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="184a1-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="184a1-124">Zprostředkovatelé identity, které publikují takový kontrolní výraz zásad měli být schopni problém tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="184a1-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184a1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="184a1-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="184a1-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="184a1-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="184a1-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="184a1-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="184a1-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="184a1-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="184a1-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="184a1-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
