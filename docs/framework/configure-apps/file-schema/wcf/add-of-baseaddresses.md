---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920221"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="80516-102">\<Přidat > \<> adres BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="80516-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="80516-103">Představuje prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="80516-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="80516-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80516-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80516-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="80516-105">\<client></span></span>  
<span data-ttu-id="80516-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="80516-106">\<endpoint></span></span>  
<span data-ttu-id="80516-107">\<host></span><span class="sxs-lookup"><span data-stu-id="80516-107">\<host></span></span>  
<span data-ttu-id="80516-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="80516-108">\<baseAddresses></span></span>  
<span data-ttu-id="80516-109">\<baseAddress – ></span><span class="sxs-lookup"><span data-stu-id="80516-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80516-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80516-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="80516-111">type</span><span class="sxs-lookup"><span data-stu-id="80516-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80516-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80516-112">Attributes and Elements</span></span>  
 <span data-ttu-id="80516-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80516-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80516-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="80516-114">Attributes</span></span>  
  
|<span data-ttu-id="80516-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="80516-115">Attribute</span></span>|<span data-ttu-id="80516-116">Popis</span><span class="sxs-lookup"><span data-stu-id="80516-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="80516-117">Řetězec, který určuje základní adresu, kterou používá hostitel služby.</span><span class="sxs-lookup"><span data-stu-id="80516-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80516-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80516-118">Child Elements</span></span>  
 <span data-ttu-id="80516-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="80516-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80516-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80516-120">Parent Elements</span></span>  
  
|<span data-ttu-id="80516-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="80516-121">Element</span></span>|<span data-ttu-id="80516-122">Popis</span><span class="sxs-lookup"><span data-stu-id="80516-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80516-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="80516-123">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="80516-124">Kolekce `baseAddress` prvků.</span><span class="sxs-lookup"><span data-stu-id="80516-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80516-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80516-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="80516-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="80516-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
