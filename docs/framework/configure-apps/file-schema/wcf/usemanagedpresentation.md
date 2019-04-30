---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769847"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="ef74d-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="ef74d-101">\<useManagedPresentation></span></span>
<span data-ttu-id="ef74d-102">Element vazby používaný ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profil WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ef74d-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="ef74d-103">Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="ef74d-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="ef74d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ef74d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ef74d-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="ef74d-105">\<bindings></span></span>  
<span data-ttu-id="ef74d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ef74d-106">\<customBinding></span></span>  
<span data-ttu-id="ef74d-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="ef74d-107">\<binding></span></span>  
<span data-ttu-id="ef74d-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="ef74d-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef74d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef74d-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef74d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ef74d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef74d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ef74d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef74d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ef74d-112">Attributes</span></span>  
 <span data-ttu-id="ef74d-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="ef74d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef74d-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ef74d-114">Child Elements</span></span>  
 <span data-ttu-id="ef74d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="ef74d-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef74d-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ef74d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ef74d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef74d-117">Element</span></span>|<span data-ttu-id="ef74d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ef74d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef74d-119">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="ef74d-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ef74d-120">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="ef74d-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef74d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef74d-121">Remarks</span></span>  
 <span data-ttu-id="ef74d-122">Tento element se používá zprostředkovatel identity pro vyjádření v jeho zásad skutečnost, že podporuje CardSpace profil WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ef74d-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="ef74d-123">Zprostředkovatelé identity, které publikují takový kontrolní výraz zásad měli být schopni problém tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="ef74d-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef74d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef74d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ef74d-125">Vazby</span><span class="sxs-lookup"><span data-stu-id="ef74d-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ef74d-126">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="ef74d-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ef74d-127">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ef74d-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ef74d-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ef74d-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
