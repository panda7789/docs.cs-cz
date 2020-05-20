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
ms.openlocfilehash: c7afe074afb9b38d6fefa1192799120dbb50b403
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442056"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="c9cdc-102">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9cdc-102">INotifySink2 Interface</span></span>
<span data-ttu-id="c9cdc-103">Deklaruje metody pro oznámení jímky.</span><span class="sxs-lookup"><span data-stu-id="c9cdc-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9cdc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c9cdc-104">Methods</span></span>  
  
|<span data-ttu-id="c9cdc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c9cdc-105">Method</span></span>|<span data-ttu-id="c9cdc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c9cdc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9cdc-107">OnSyncCallEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="c9cdc-107">OnSyncCallEnter Method</span></span>](inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="c9cdc-108">Vyvolá se při vstupu volání.</span><span class="sxs-lookup"><span data-stu-id="c9cdc-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="c9cdc-109">OnSyncCallExit – metoda</span><span class="sxs-lookup"><span data-stu-id="c9cdc-109">OnSyncCallExit Method</span></span>](inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="c9cdc-110">Vyvolá se při ukončení volání.</span><span class="sxs-lookup"><span data-stu-id="c9cdc-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="c9cdc-111">OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="c9cdc-111">OnSyncCallOut Method</span></span>](inotifysink2-onsynccallout-method.md)|<span data-ttu-id="c9cdc-112">Vyvolá se, když je volání ven.</span><span class="sxs-lookup"><span data-stu-id="c9cdc-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="c9cdc-113">OnSyncCallReturn – metoda</span><span class="sxs-lookup"><span data-stu-id="c9cdc-113">OnSyncCallReturn Method</span></span>](inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="c9cdc-114">Vyvolá se, když se volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="c9cdc-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9cdc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9cdc-115">Requirements</span></span>  
 <span data-ttu-id="c9cdc-116">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="c9cdc-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9cdc-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9cdc-117">See also</span></span>

- [<span data-ttu-id="c9cdc-118">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9cdc-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="c9cdc-119">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9cdc-119">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="c9cdc-120">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="c9cdc-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
