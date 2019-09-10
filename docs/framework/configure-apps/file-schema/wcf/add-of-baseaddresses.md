---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850593"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="abdad-102">\<Přidat > \<> adres BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="abdad-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="abdad-103">Představuje prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="abdad-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="abdad-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="abdad-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="abdad-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="abdad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="abdad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="abdad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adres BaseAddresses >** ](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="abdad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="abdad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="abdad-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdad-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abdad-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="abdad-112">type</span><span class="sxs-lookup"><span data-stu-id="abdad-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abdad-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abdad-113">Attributes and Elements</span></span>  
 <span data-ttu-id="abdad-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abdad-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abdad-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="abdad-115">Attributes</span></span>  
  
|<span data-ttu-id="abdad-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="abdad-116">Attribute</span></span>|<span data-ttu-id="abdad-117">Popis</span><span class="sxs-lookup"><span data-stu-id="abdad-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="abdad-118">Řetězec, který určuje základní adresu, kterou používá hostitel služby.</span><span class="sxs-lookup"><span data-stu-id="abdad-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abdad-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="abdad-119">Child Elements</span></span>  
 <span data-ttu-id="abdad-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="abdad-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abdad-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="abdad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="abdad-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="abdad-122">Element</span></span>|<span data-ttu-id="abdad-123">Popis</span><span class="sxs-lookup"><span data-stu-id="abdad-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abdad-124">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="abdad-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="abdad-125">Kolekce `baseAddress` prvků.</span><span class="sxs-lookup"><span data-stu-id="abdad-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abdad-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abdad-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="abdad-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="abdad-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
