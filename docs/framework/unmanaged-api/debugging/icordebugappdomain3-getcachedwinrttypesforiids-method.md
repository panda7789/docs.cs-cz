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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef8d1c47275d3cbd69c1516b788b950f8535513
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737718"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="7e116-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="7e116-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="7e116-103">Získá enumerátor pro uložené v mezipaměti typy Windows Runtime v doméně aplikace podle jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7e116-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e116-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e116-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e116-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="7e116-106">[in] Počet požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="7e116-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="7e116-107">[in] Ukazatel na pole, které obsahuje rozhraní identifikátory odpovídající spravované reprezentace typů prostředí Windows Runtime se má načíst.</span><span class="sxs-lookup"><span data-stu-id="7e116-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="7e116-108">[out] Načte ukazatel na adresu objektu rozhraní "icordebugtypeenum –", který umožňuje výčtu v mezipaměti spravované reprezentace typů prostředí Windows Runtime, založené na rozhraní identifikátory v `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="7e116-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e116-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e116-109">Remarks</span></span>  
 <span data-ttu-id="7e116-110">Jestliže metoda selže načíst informace pro konkrétní rozhraní identifikátor, odpovídající položku v kolekci "Icordebugtypeenum –" bude mít typ `ELEMENT_TYPE_END` chyby kvůli problémům s načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé rozhraní identifikátory.</span><span class="sxs-lookup"><span data-stu-id="7e116-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e116-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e116-111">Requirements</span></span>  
 <span data-ttu-id="7e116-112">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="7e116-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7e116-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e116-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e116-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e116-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e116-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e116-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e116-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e116-116">See also</span></span>

- [<span data-ttu-id="7e116-117">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e116-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
