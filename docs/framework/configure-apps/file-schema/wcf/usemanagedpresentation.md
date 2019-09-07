---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399215"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="e05d9-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="e05d9-101">\<useManagedPresentation></span></span>
<span data-ttu-id="e05d9-102">Prvek vazby, který slouží ke komunikaci se službou tokenu zabezpečení služby CardSpace, který podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e05d9-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e05d9-103">Tento element nemá žádný atribut a je přítomný jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="e05d9-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="e05d9-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e05d9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e05d9-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e05d9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e05d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e05d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e05d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e05d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e05d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="e05d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e05d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="e05d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05d9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e05d9-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e05d9-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e05d9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e05d9-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e05d9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e05d9-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e05d9-113">Attributes</span></span>  
 <span data-ttu-id="e05d9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e05d9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e05d9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e05d9-115">Child Elements</span></span>  
 <span data-ttu-id="e05d9-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e05d9-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e05d9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e05d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e05d9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e05d9-118">Element</span></span>|<span data-ttu-id="e05d9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e05d9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e05d9-120">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e05d9-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e05d9-121">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="e05d9-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e05d9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e05d9-122">Remarks</span></span>  
 <span data-ttu-id="e05d9-123">Tento prvek používá zprostředkovatel identity ke expresi v jeho zásadě fakt, že podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e05d9-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e05d9-124">Zprostředkovatelé identity, kteří publikují takový kontrolní výraz zásad, by měli mít schopnost vystavit tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="e05d9-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05d9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e05d9-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e05d9-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="e05d9-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e05d9-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="e05d9-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e05d9-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="e05d9-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e05d9-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e05d9-129">\<customBinding></span></span>](custombinding.md)
