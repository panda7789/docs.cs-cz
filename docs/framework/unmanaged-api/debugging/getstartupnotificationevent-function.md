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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698197"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="8fad5-102">GetStartupNotificationEvent – funkce</span><span class="sxs-lookup"><span data-stu-id="8fad5-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="8fad5-103">Vytvoří nebo otevře popisovač události, která bude být signalizován při libovolné CLR (CLR), který se načítá do zadaného cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="8fad5-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fad5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fad5-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fad5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fad5-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="8fad5-106">[in] Zpracovat identifikátor cílového procesu, ze kterého chcete dostávat oznámení při spuštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8fad5-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="8fad5-107">[out] Ukazatel na popisovač, který bude signalizován pomocí modulu CLR při spuštění.</span><span class="sxs-lookup"><span data-stu-id="8fad5-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fad5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8fad5-108">Return Value</span></span>  
 <span data-ttu-id="8fad5-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fad5-109">S_OK</span></span>  
 <span data-ttu-id="8fad5-110">Byly úspěšně načteny popisovač události oznámení při spuštění.</span><span class="sxs-lookup"><span data-stu-id="8fad5-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="8fad5-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8fad5-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="8fad5-112">`phStartupEvent` má hodnotu null nebo `debuggeePID` neodkazuje na proces, který aktuálně běží.</span><span class="sxs-lookup"><span data-stu-id="8fad5-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="8fad5-113">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="8fad5-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8fad5-114">Nepovedlo se získat popisovač události oznámení při spuštění.</span><span class="sxs-lookup"><span data-stu-id="8fad5-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fad5-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fad5-115">Remarks</span></span>  
 <span data-ttu-id="8fad5-116">V operačním systému Windows `debuggeePID` mapuje na operační systém zpracovávat identifikátor.</span><span class="sxs-lookup"><span data-stu-id="8fad5-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="8fad5-117">Událost je signalizována před jakoukoli Spravované, že kód je proveden součástí CLR, který signál události.</span><span class="sxs-lookup"><span data-stu-id="8fad5-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fad5-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fad5-118">Requirements</span></span>  
 <span data-ttu-id="8fad5-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fad5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fad5-120">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="8fad5-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="8fad5-121">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="8fad5-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="8fad5-122">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="8fad5-122">**.NET Framework Versions:** 3.5 SP1</span></span>
