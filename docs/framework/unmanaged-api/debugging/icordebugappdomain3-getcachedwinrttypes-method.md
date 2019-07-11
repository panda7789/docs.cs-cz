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
ms.openlocfilehash: 4ba981d86f90af449820ce13aa847169ca877429
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737770"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="aea92-102">ICorDebugAppDomain3::GetCachedWinRTTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="aea92-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="aea92-103">Získá enumerátor pro všechny typy v mezipaměti prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="aea92-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aea92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aea92-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="aea92-106">[out] Ukazatel [icordebugguidtotypeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) rozhraní objektu, který můžete zobrazit výčet spravované reprezentace typů prostředí Windows Runtime nyní načteny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="aea92-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea92-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aea92-107">Requirements</span></span>  
 <span data-ttu-id="aea92-108">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="aea92-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="aea92-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aea92-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aea92-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aea92-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aea92-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea92-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea92-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aea92-112">See also</span></span>

- [<span data-ttu-id="aea92-113">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aea92-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
