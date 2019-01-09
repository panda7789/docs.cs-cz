---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 5bd2356c3bb798e948341cb3c4ba504ac886ed44
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145078"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="84f88-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="84f88-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="84f88-103">Určuje ladění služby pro objekt zpětného volání Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="84f88-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="84f88-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84f88-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84f88-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="84f88-105">\<behaviors></span></span>  
<span data-ttu-id="84f88-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="84f88-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="84f88-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="84f88-107">\<behavior></span></span>  
<span data-ttu-id="84f88-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="84f88-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f88-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84f88-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="84f88-110">Typ</span><span class="sxs-lookup"><span data-stu-id="84f88-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84f88-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="84f88-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84f88-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="84f88-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84f88-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="84f88-113">Attributes</span></span>  
  
|<span data-ttu-id="84f88-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="84f88-114">Attribute</span></span>|<span data-ttu-id="84f88-115">Popis</span><span class="sxs-lookup"><span data-stu-id="84f88-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="84f88-116">Hodnota, která určuje, zda objekty zpětného volání klienta vrátí informace o spravované výjimce v chyb SOAP zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="84f88-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="84f88-117">Pokud tento atribut nastavíte na `true` můžete prostřednictvím kódu programu, může být povolen tok informací o řízené výjimce do objektu zpětného volání klienta zpět do služby pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="84f88-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="84f88-118">**Upozornění:**  Vracející informace o spravované výjimce klientům může představovat bezpečnostní riziko.</span><span class="sxs-lookup"><span data-stu-id="84f88-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="84f88-119">Je to proto, že podrobnosti o výjimce zveřejnit informace o implementaci vnitřní chybě služby, které by mohly používat neoprávněným klientů.</span><span class="sxs-lookup"><span data-stu-id="84f88-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84f88-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="84f88-120">Child Elements</span></span>  
 <span data-ttu-id="84f88-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="84f88-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84f88-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="84f88-122">Parent Elements</span></span>  
  
|<span data-ttu-id="84f88-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="84f88-123">Element</span></span>|<span data-ttu-id="84f88-124">Popis</span><span class="sxs-lookup"><span data-stu-id="84f88-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84f88-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="84f88-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="84f88-126">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="84f88-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84f88-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="84f88-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
