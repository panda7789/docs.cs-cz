---
title: 'ICorDebugVariableHomeEnum:: Next – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121924"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="29af1-102">ICorDebugVariableHomeEnum:: Next – metoda</span><span class="sxs-lookup"><span data-stu-id="29af1-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="29af1-103">Získá zadaný počet instancí [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="29af1-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29af1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29af1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29af1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29af1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="29af1-106">pro Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="29af1-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="29af1-107">Pole ukazatelů, z nichž každý odkazuje na objekt [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , který poskytuje informace o lokální proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="29af1-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="29af1-108">mimo Počet instancí skutečně vrácených v objektech.</span><span class="sxs-lookup"><span data-stu-id="29af1-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29af1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29af1-109">Return Value</span></span>  
 <span data-ttu-id="29af1-110">Metoda vrací následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29af1-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="29af1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29af1-111">HRESULT</span></span>|<span data-ttu-id="29af1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="29af1-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29af1-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="29af1-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29af1-114">Skutečný počet načtených instancí, jak se odráží v `pceltFetched`, je menší než počet požadovaných instancí.</span><span class="sxs-lookup"><span data-stu-id="29af1-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29af1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29af1-115">Remarks</span></span>  
 <span data-ttu-id="29af1-116">Metoda [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) načte maximálně `celt` objektů počínaje aktuální pozicí čítače.</span><span class="sxs-lookup"><span data-stu-id="29af1-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="29af1-117">Když se metoda vrátí, `pceltFetched` obsahuje skutečný počet načtených objektů.</span><span class="sxs-lookup"><span data-stu-id="29af1-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29af1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29af1-118">Requirements</span></span>  
 <span data-ttu-id="29af1-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29af1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29af1-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29af1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29af1-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29af1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29af1-122">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29af1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29af1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29af1-123">See also</span></span>

- [<span data-ttu-id="29af1-124">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29af1-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="29af1-125">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29af1-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
