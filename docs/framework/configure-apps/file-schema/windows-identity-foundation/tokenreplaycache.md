---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944080"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="8b3ac-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="8b3ac-101">\<tokenReplayCache></span></span>
<span data-ttu-id="8b3ac-102">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="8b3ac-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8b3ac-103">\<system.identityModel></span></span>  
<span data-ttu-id="8b3ac-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b3ac-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8b3ac-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="8b3ac-105">\<caches></span></span>  
<span data-ttu-id="8b3ac-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="8b3ac-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b3ac-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b3ac-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b3ac-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8b3ac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8b3ac-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b3ac-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8b3ac-110">Attributes</span></span>  
  
|<span data-ttu-id="8b3ac-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8b3ac-111">Attribute</span></span>|<span data-ttu-id="8b3ac-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8b3ac-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b3ac-113">– typ</span><span class="sxs-lookup"><span data-stu-id="8b3ac-113">type</span></span>|<span data-ttu-id="8b3ac-114">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="8b3ac-115">Další informace o tom, jak zadat vlastní `type`, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="8b3ac-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="8b3ac-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8b3ac-116">Child Elements</span></span>  
 <span data-ttu-id="8b3ac-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b3ac-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b3ac-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8b3ac-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8b3ac-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="8b3ac-119">Element</span></span>|<span data-ttu-id="8b3ac-120">Popis</span><span class="sxs-lookup"><span data-stu-id="8b3ac-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b3ac-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="8b3ac-121">\<caches></span></span>](caches.md)|<span data-ttu-id="8b3ac-122">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b3ac-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b3ac-123">Remarks</span></span>  
 <span data-ttu-id="8b3ac-124">Mezipaměť pro opětovné přehrání tokenu se používá ke zjišťování předaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="8b3ac-125">Detekce opětovného přehrání tokenu je povolena [ \<prvkem tokenReplayDetection >](tokenreplaydetection.md) , který také určuje maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-125">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b3ac-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b3ac-126">Example</span></span>  
 <span data-ttu-id="8b3ac-127">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro detekci přehráných tokenů.</span><span class="sxs-lookup"><span data-stu-id="8b3ac-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b3ac-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b3ac-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="8b3ac-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="8b3ac-129">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
