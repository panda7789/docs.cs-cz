---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956868"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="279bf-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="279bf-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="279bf-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="279bf-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="279bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="279bf-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="279bf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="279bf-105">Methods</span></span>  
 <span data-ttu-id="279bf-106">Třídy ServiceThrottlingBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="279bf-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="279bf-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="279bf-107">Properties</span></span>  
 <span data-ttu-id="279bf-108">Třídy ServiceThrottlingBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="279bf-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="279bf-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="279bf-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="279bf-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="279bf-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="279bf-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="279bf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="279bf-112">Maximální počet zpráv aktivně pracujících přes veškeré objekty odesílatele v ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="279bf-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="279bf-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="279bf-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="279bf-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="279bf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="279bf-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="279bf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="279bf-116">Maximální počet objektů služeb, které můžete provést najednou.</span><span class="sxs-lookup"><span data-stu-id="279bf-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="279bf-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="279bf-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="279bf-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="279bf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="279bf-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="279bf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="279bf-120">Maximální počet relací, které může hostitel najednou přijmout.</span><span class="sxs-lookup"><span data-stu-id="279bf-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="279bf-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="279bf-121">Requirements</span></span>  
  
|<span data-ttu-id="279bf-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="279bf-122">MOF</span></span>|<span data-ttu-id="279bf-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="279bf-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="279bf-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="279bf-124">Namespace</span></span>|<span data-ttu-id="279bf-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="279bf-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="279bf-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="279bf-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
