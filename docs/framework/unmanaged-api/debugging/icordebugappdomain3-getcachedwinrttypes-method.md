---
title: ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7d152edac34449a08b4bcfbe5525b63abcba0fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480764"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="9d6bf-102">ICorDebugAppDomain3::GetCachedWinRTTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="9d6bf-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="9d6bf-103">Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6bf-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6bf-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="9d6bf-106">[out] Ukazatel [icordebugguidtotypeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) objektu rozhraní, které můžete zobrazit výčet spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy aktuálně načtené v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9d6bf-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6bf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d6bf-107">Requirements</span></span>  
 <span data-ttu-id="9d6bf-108">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6bf-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="9d6bf-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d6bf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d6bf-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d6bf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d6bf-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6bf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6bf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d6bf-112">See also</span></span>
- [<span data-ttu-id="9d6bf-113">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d6bf-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
