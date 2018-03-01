---
title: "ICorDebugProcess3::SetEnableCustomNotification – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ccd1f4b6be56202d5efea1d2e38dce554835218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="f337e-102">ICorDebugProcess3::SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="f337e-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="f337e-103">Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="f337e-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f337e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f337e-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f337e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f337e-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f337e-106">[v] Typ, který určuje vlastní ladicí program oznámení.</span><span class="sxs-lookup"><span data-stu-id="f337e-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="f337e-107">[v] `true` povolit vlastní ladicí program oznámení; `false` zakázat oznámení.</span><span class="sxs-lookup"><span data-stu-id="f337e-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="f337e-108">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f337e-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f337e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f337e-109">Remarks</span></span>  
 <span data-ttu-id="f337e-110">Když `fEnable` je nastaven na `true`, volá, aby se <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoda aktivační událost [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f337e-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="f337e-111">Oznámení jsou zakázané ve výchozím nastavení; ladicí program proto musíte zadat všechny typy oznámení, že zná a chce zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f337e-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="f337e-112">Protože [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) třída má obor doménu aplikace, musí volat ladicího programu `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chcete dostávat oznámení napříč celý proces.</span><span class="sxs-lookup"><span data-stu-id="f337e-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="f337e-113">Od verze [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], jen podporované oznámení je závislost mezi vlákny oznámení.</span><span class="sxs-lookup"><span data-stu-id="f337e-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f337e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f337e-114">Requirements</span></span>  
 <span data-ttu-id="f337e-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f337e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f337e-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f337e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f337e-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f337e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f337e-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f337e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f337e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f337e-119">See Also</span></span>  
 [<span data-ttu-id="f337e-120">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f337e-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="f337e-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f337e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f337e-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="f337e-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
