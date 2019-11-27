---
title: INotifySink2 – rozhraní
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: af50c82974b779b901135795f37e3bd4c8b8c156
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440980"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="4cc81-102">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cc81-102">INotifySink2 Interface</span></span>
<span data-ttu-id="4cc81-103">Deklaruje metody pro oznámení jímky.</span><span class="sxs-lookup"><span data-stu-id="4cc81-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cc81-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4cc81-104">Methods</span></span>  
  
|<span data-ttu-id="4cc81-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4cc81-105">Method</span></span>|<span data-ttu-id="4cc81-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4cc81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cc81-107">OnSyncCallEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="4cc81-107">OnSyncCallEnter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="4cc81-108">Vyvolá se při vstupu volání.</span><span class="sxs-lookup"><span data-stu-id="4cc81-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="4cc81-109">OnSyncCallExit – metoda</span><span class="sxs-lookup"><span data-stu-id="4cc81-109">OnSyncCallExit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="4cc81-110">Vyvolá se při ukončení volání.</span><span class="sxs-lookup"><span data-stu-id="4cc81-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="4cc81-111">OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="4cc81-111">OnSyncCallOut Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|<span data-ttu-id="4cc81-112">Vyvolá se, když je volání ven.</span><span class="sxs-lookup"><span data-stu-id="4cc81-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="4cc81-113">OnSyncCallReturn – metoda</span><span class="sxs-lookup"><span data-stu-id="4cc81-113">OnSyncCallReturn Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="4cc81-114">Vyvolá se, když se volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="4cc81-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cc81-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cc81-115">Requirements</span></span>  
 <span data-ttu-id="4cc81-116">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="4cc81-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc81-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cc81-117">See also</span></span>

- [<span data-ttu-id="4cc81-118">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cc81-118">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="4cc81-119">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cc81-119">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="4cc81-120">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="4cc81-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
