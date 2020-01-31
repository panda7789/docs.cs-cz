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
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785002"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="ef0f4-102">ICorDebugAppDomain3::GetCachedWinRTTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="ef0f4-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="ef0f4-103">Získá enumerátor pro všechny typy prostředí Windows Runtime v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef0f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef0f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef0f4-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="ef0f4-106">mimo Ukazatel na objekt rozhraní [ICorDebugGuidToTypeEnum –](icordebugguidtotypeenum-interface.md) , který může vyčíslit spravované reprezentace prostředí Windows runtimech typů, které jsou aktuálně načteny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef0f4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef0f4-107">Requirements</span></span>  
 <span data-ttu-id="ef0f4-108">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="ef0f4-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="ef0f4-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef0f4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef0f4-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ef0f4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef0f4-111">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef0f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0f4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef0f4-112">See also</span></span>

- [<span data-ttu-id="ef0f4-113">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef0f4-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
