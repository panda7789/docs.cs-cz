---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088883"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="3368d-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="3368d-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="3368d-103">Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3368d-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3368d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3368d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3368d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3368d-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="3368d-106">pro Počet požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="3368d-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="3368d-107">pro Ukazatel na pole, které obsahuje identifikátory rozhraní odpovídající spravovaným reprezentacím typů prostředí Windows Runtime, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="3368d-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="3368d-108">mimo Ukazatel na adresu objektu rozhraní "ICorDebugTypeEnum", která umožňuje vyhodnotit výčet spravovaných reprezentace typů prostředí Windows Runtime uložených v mezipaměti, na základě identifikátorů rozhraní v `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="3368d-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3368d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3368d-109">Remarks</span></span>  
 <span data-ttu-id="3368d-110">Pokud metoda nepovede načíst informace pro konkrétní identifikátor rozhraní, odpovídající položka v kolekci "ICorDebugTypeEnum" bude mít typ `ELEMENT_TYPE_END` chyby z důvodu problémů načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé identifikátory rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3368d-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3368d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3368d-111">Requirements</span></span>  
 <span data-ttu-id="3368d-112">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="3368d-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3368d-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3368d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3368d-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3368d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3368d-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3368d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3368d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3368d-116">See also</span></span>

- [<span data-ttu-id="3368d-117">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3368d-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
