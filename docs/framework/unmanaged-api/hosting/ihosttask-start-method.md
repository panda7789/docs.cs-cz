---
title: IHostTask::Start – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: a4e8211f091b2a3a4f24d8350f6d7dbe7d7920af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842384"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="8483b-102">IHostTask::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="8483b-102">IHostTask::Start Method</span></span>
<span data-ttu-id="8483b-103">Požaduje, aby hostitel přesunul úlohu představovanou aktuální instancí [IHostTask](ihosttask-interface.md) z pozastaveného do aktivního stavu, ve kterém lze spustit kód.</span><span class="sxs-lookup"><span data-stu-id="8483b-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8483b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8483b-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8483b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8483b-105">Return Value</span></span>  
  
|<span data-ttu-id="8483b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8483b-106">HRESULT</span></span>|<span data-ttu-id="8483b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8483b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8483b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8483b-108">S_OK</span></span>|<span data-ttu-id="8483b-109">Začátek se úspěšně vrátil.</span><span class="sxs-lookup"><span data-stu-id="8483b-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="8483b-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8483b-110">E_FAIL</span></span>|<span data-ttu-id="8483b-111">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8483b-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8483b-112">Když metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8483b-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="8483b-113">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8483b-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8483b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8483b-114">Remarks</span></span>  
 <span data-ttu-id="8483b-115">`Start`vždy vrátí hodnotu HRESULT S_OK, s výjimkou případů, kdy došlo k závažným chybám.</span><span class="sxs-lookup"><span data-stu-id="8483b-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8483b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8483b-116">Requirements</span></span>  
 <span data-ttu-id="8483b-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8483b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8483b-118">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8483b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8483b-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8483b-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8483b-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8483b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8483b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8483b-121">See also</span></span>

- [<span data-ttu-id="8483b-122">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8483b-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8483b-123">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8483b-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8483b-124">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8483b-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8483b-125">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8483b-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
