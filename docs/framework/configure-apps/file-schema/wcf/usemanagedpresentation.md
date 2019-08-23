---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940616"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="b9d59-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="b9d59-101">\<useManagedPresentation></span></span>
<span data-ttu-id="b9d59-102">Prvek vazby, který slouží ke komunikaci se službou tokenu zabezpečení služby CardSpace, který podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b9d59-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b9d59-103">Tento element nemá žádný atribut a je přítomný jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="b9d59-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="b9d59-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9d59-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b9d59-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="b9d59-105">\<bindings></span></span>  
<span data-ttu-id="b9d59-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b9d59-106">\<customBinding></span></span>  
<span data-ttu-id="b9d59-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="b9d59-107">\<binding></span></span>  
<span data-ttu-id="b9d59-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="b9d59-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d59-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9d59-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9d59-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9d59-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b9d59-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9d59-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9d59-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9d59-112">Attributes</span></span>  
 <span data-ttu-id="b9d59-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9d59-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9d59-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9d59-114">Child Elements</span></span>  
 <span data-ttu-id="b9d59-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9d59-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9d59-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9d59-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b9d59-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9d59-117">Element</span></span>|<span data-ttu-id="b9d59-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b9d59-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9d59-119">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="b9d59-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b9d59-120">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b9d59-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9d59-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9d59-121">Remarks</span></span>  
 <span data-ttu-id="b9d59-122">Tento prvek používá zprostředkovatel identity ke expresi v jeho zásadě fakt, že podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b9d59-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b9d59-123">Zprostředkovatelé identity, kteří publikují takový kontrolní výraz zásad, by měli mít schopnost vystavit tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="b9d59-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d59-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9d59-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b9d59-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="b9d59-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9d59-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="b9d59-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b9d59-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b9d59-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b9d59-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b9d59-128">\<customBinding></span></span>](custombinding.md)
