---
title: ICorDebugProcess3::SetEnableCustomNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7501a8a0f8368049c87b3c90e1e707e12773a853
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531639"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="bacc6-102">ICorDebugProcess3::SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="bacc6-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="bacc6-103">Povolí nebo zakáže vlastní oznámení ladicího programu zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="bacc6-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bacc6-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bacc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bacc6-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="bacc6-106">[in] Typ, který určuje vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="bacc6-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="bacc6-107">[in] `true` povolit vlastní oznámení ladicího programu; `false` zakázat oznámení.</span><span class="sxs-lookup"><span data-stu-id="bacc6-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="bacc6-108">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bacc6-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bacc6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bacc6-109">Remarks</span></span>  
 <span data-ttu-id="bacc6-110">Při `fEnable` je nastavena na `true`, volání <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoda triggeru [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bacc6-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="bacc6-111">Oznámení jsou ve výchozím nastavení; zakázána. ladicí program, proto musíte zadat všechny typy upozornění ví o a chce zpracovat.</span><span class="sxs-lookup"><span data-stu-id="bacc6-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="bacc6-112">Protože [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) třídy je omezené podle domény aplikace, ladicí program musí volat `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chce, abyste dostávali oznámení napříč celým procesem.</span><span class="sxs-lookup"><span data-stu-id="bacc6-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="bacc6-113">Počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], jen podporované oznámení, je oznámení závislostí mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="bacc6-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bacc6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bacc6-114">Requirements</span></span>  
 <span data-ttu-id="bacc6-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bacc6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bacc6-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bacc6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bacc6-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bacc6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bacc6-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bacc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacc6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bacc6-119">See also</span></span>
- [<span data-ttu-id="bacc6-120">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bacc6-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="bacc6-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bacc6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bacc6-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="bacc6-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
