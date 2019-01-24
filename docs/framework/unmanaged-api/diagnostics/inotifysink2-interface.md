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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc5d09ac12919b8c68b9fe4bf9f7dc0009b2d4b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705466"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="b16ab-102">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b16ab-102">INotifySink2 Interface</span></span>
<span data-ttu-id="b16ab-103">Deklaruje metody pro jímku oznámení.</span><span class="sxs-lookup"><span data-stu-id="b16ab-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b16ab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b16ab-104">Methods</span></span>  
  
|<span data-ttu-id="b16ab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b16ab-105">Method</span></span>|<span data-ttu-id="b16ab-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b16ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b16ab-107">OnSyncCallEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="b16ab-107">OnSyncCallEnter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="b16ab-108">Získá vyvolána při vstupu do volání.</span><span class="sxs-lookup"><span data-stu-id="b16ab-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="b16ab-109">OnSyncCallExit – metoda</span><span class="sxs-lookup"><span data-stu-id="b16ab-109">OnSyncCallExit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="b16ab-110">Získá vyvolána při ukončení volání.</span><span class="sxs-lookup"><span data-stu-id="b16ab-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="b16ab-111">OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="b16ab-111">OnSyncCallOut Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|<span data-ttu-id="b16ab-112">Získá vyvolán při volání je navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="b16ab-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="b16ab-113">OnSyncCallReturn – metoda</span><span class="sxs-lookup"><span data-stu-id="b16ab-113">OnSyncCallReturn Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="b16ab-114">Získá vyvolán při volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="b16ab-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b16ab-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b16ab-115">Requirements</span></span>  
 <span data-ttu-id="b16ab-116">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b16ab-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16ab-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b16ab-117">See also</span></span>
- [<span data-ttu-id="b16ab-118">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b16ab-118">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="b16ab-119">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b16ab-119">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="b16ab-120">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="b16ab-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
