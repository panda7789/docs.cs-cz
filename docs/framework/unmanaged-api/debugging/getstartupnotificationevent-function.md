---
title: "GetStartupNotificationEvent – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 809f34d265e0a1677d8b7fc78515b20df7353968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="3980c-102">GetStartupNotificationEvent – funkce</span><span class="sxs-lookup"><span data-stu-id="3980c-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="3980c-103">Vytvoří nebo otevře popisovač události, který se bude dát signál při jakékoli modul common language runtime (CLR), se načítá v zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="3980c-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3980c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3980c-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3980c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3980c-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="3980c-106">[v] Proces identifikátor tento cílový proces, ze kterého chcete dostávat oznámení spuštění CLR.</span><span class="sxs-lookup"><span data-stu-id="3980c-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="3980c-107">[out] Ukazatel na popisovač, který bude signál pomocí modulu CLR při spuštění.</span><span class="sxs-lookup"><span data-stu-id="3980c-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3980c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3980c-108">Return Value</span></span>  
 <span data-ttu-id="3980c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="3980c-109">S_OK</span></span>  
 <span data-ttu-id="3980c-110">Byly úspěšně načteny popisovač událost upozornění na spuštění.</span><span class="sxs-lookup"><span data-stu-id="3980c-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="3980c-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3980c-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="3980c-112">`phStartupEvent`má hodnotu null nebo `debuggeePID` neodkazuje na procesu, který je aktuálně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3980c-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="3980c-113">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="3980c-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3980c-114">Nepodařilo se získat popisovač událost upozornění na spuštění.</span><span class="sxs-lookup"><span data-stu-id="3980c-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3980c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3980c-115">Remarks</span></span>  
 <span data-ttu-id="3980c-116">V operačním systému Windows `debuggeePID` mapuje operační systém zpracovat identifikátor.</span><span class="sxs-lookup"><span data-stu-id="3980c-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="3980c-117">Událost signalizace před spuštěním spravované, že je kód spuštěn pomocí modulu CLR, který signál události.</span><span class="sxs-lookup"><span data-stu-id="3980c-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3980c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3980c-118">Requirements</span></span>  
 <span data-ttu-id="3980c-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3980c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3980c-120">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="3980c-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="3980c-121">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="3980c-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="3980c-122">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3980c-122">**.NET Framework Versions:** 3.5 SP1</span></span>
