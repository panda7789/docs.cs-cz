---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771766"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="3f5f0-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3f5f0-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="3f5f0-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3f5f0-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f5f0-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3f5f0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3f5f0-105">Methods</span></span>  
 <span data-ttu-id="3f5f0-106">Třídy ServiceThrottlingBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="3f5f0-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3f5f0-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3f5f0-107">Properties</span></span>  
 <span data-ttu-id="3f5f0-108">Třídy ServiceThrottlingBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3f5f0-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="3f5f0-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="3f5f0-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="3f5f0-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="3f5f0-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="3f5f0-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3f5f0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f5f0-112">Maximální počet zpráv aktivně pracujících přes veškeré objekty odesílatele v ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="3f5f0-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="3f5f0-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="3f5f0-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="3f5f0-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="3f5f0-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="3f5f0-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3f5f0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f5f0-116">Maximální počet objektů služeb, které můžete provést najednou.</span><span class="sxs-lookup"><span data-stu-id="3f5f0-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="3f5f0-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="3f5f0-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="3f5f0-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="3f5f0-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3f5f0-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3f5f0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f5f0-120">Maximální počet relací, které může hostitel najednou přijmout.</span><span class="sxs-lookup"><span data-stu-id="3f5f0-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f5f0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f5f0-121">Requirements</span></span>  
  
|<span data-ttu-id="3f5f0-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="3f5f0-122">MOF</span></span>|<span data-ttu-id="3f5f0-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3f5f0-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3f5f0-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3f5f0-124">Namespace</span></span>|<span data-ttu-id="3f5f0-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3f5f0-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f5f0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f5f0-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
