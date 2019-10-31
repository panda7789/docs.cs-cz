---
title: GetStartupNotificationEvent – funkce
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122954"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="051d8-102">GetStartupNotificationEvent – funkce</span><span class="sxs-lookup"><span data-stu-id="051d8-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="051d8-103">Vytvoří nebo otevře obslužnou rutinu události, která bude signalizována jakýmkoli modulem CLR (Common Language Runtime), který se načítá v zadaném cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="051d8-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="051d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="051d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="051d8-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="051d8-106">pro Identifikátor procesu cílového procesu, ze kterého mají být přijímána oznámení o spuštění CLR.</span><span class="sxs-lookup"><span data-stu-id="051d8-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="051d8-107">mimo Ukazatel na popisovač, který bude při spuštění signalizoval modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="051d8-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="051d8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="051d8-108">Return Value</span></span>  
 <span data-ttu-id="051d8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="051d8-109">S_OK</span></span>  
 <span data-ttu-id="051d8-110">Úspěšně se získal popisovač události oznámení při spuštění.</span><span class="sxs-lookup"><span data-stu-id="051d8-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="051d8-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="051d8-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="051d8-112">`phStartupEvent` je null nebo `debuggeePID` neodkazuje na proces, který aktuálně běží.</span><span class="sxs-lookup"><span data-stu-id="051d8-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="051d8-113">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="051d8-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="051d8-114">Nelze získat popisovač události oznámení při spuštění.</span><span class="sxs-lookup"><span data-stu-id="051d8-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="051d8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="051d8-115">Remarks</span></span>  
 <span data-ttu-id="051d8-116">V operačním systému Windows `debuggeePID` mapuje identifikátor procesu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="051d8-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="051d8-117">Událost je signalizována před spuštěním jakéhokoliv spravovaného kódu modulem CLR, který signalizace událost.</span><span class="sxs-lookup"><span data-stu-id="051d8-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="051d8-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="051d8-118">Requirements</span></span>  
 <span data-ttu-id="051d8-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="051d8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="051d8-120">**Záhlaví:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="051d8-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="051d8-121">**Knihovna:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="051d8-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="051d8-122">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="051d8-122">**.NET Framework Versions:** 3.5 SP1</span></span>
