---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: edc154fcce0058455f1376a2a45807c92f7f2457
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190947"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="31c1f-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="31c1f-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="31c1f-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="31c1f-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31c1f-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="31c1f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="31c1f-105">Methods</span></span>  
 <span data-ttu-id="31c1f-106">Třídy ServiceThrottlingBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="31c1f-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="31c1f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="31c1f-107">Properties</span></span>  
 <span data-ttu-id="31c1f-108">Třídy ServiceThrottlingBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="31c1f-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="31c1f-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="31c1f-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="31c1f-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="31c1f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="31c1f-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="31c1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="31c1f-112">Maximální počet zpráv aktivně pracujících přes veškeré objekty odesílatele v ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="31c1f-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="31c1f-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="31c1f-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="31c1f-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="31c1f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="31c1f-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="31c1f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="31c1f-116">Maximální počet objektů služeb, které můžete provést najednou.</span><span class="sxs-lookup"><span data-stu-id="31c1f-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="31c1f-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="31c1f-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="31c1f-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="31c1f-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="31c1f-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="31c1f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="31c1f-120">Maximální počet relací, které může hostitel najednou přijmout.</span><span class="sxs-lookup"><span data-stu-id="31c1f-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c1f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31c1f-121">Requirements</span></span>  
  
|<span data-ttu-id="31c1f-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="31c1f-122">MOF</span></span>|<span data-ttu-id="31c1f-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="31c1f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="31c1f-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="31c1f-124">Namespace</span></span>|<span data-ttu-id="31c1f-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="31c1f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31c1f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="31c1f-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
