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
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025902"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="c03cf-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="c03cf-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="c03cf-103">Získá enumerátor pro uložené v mezipaměti typy Windows Runtime v doméně aplikace podle jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c03cf-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c03cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c03cf-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c03cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c03cf-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="c03cf-106">[in] Počet požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="c03cf-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="c03cf-107">[in] Ukazatel na pole, které obsahuje rozhraní identifikátory odpovídající spravované reprezentace typů prostředí Windows Runtime se má načíst.</span><span class="sxs-lookup"><span data-stu-id="c03cf-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="c03cf-108">[out] Načte ukazatel na adresu objektu rozhraní "icordebugtypeenum –", který umožňuje výčtu v mezipaměti spravované reprezentace typů prostředí Windows Runtime, založené na rozhraní identifikátory v `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="c03cf-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c03cf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c03cf-109">Remarks</span></span>  
 <span data-ttu-id="c03cf-110">Jestliže metoda selže načíst informace pro konkrétní rozhraní identifikátor, odpovídající položku v kolekci "Icordebugtypeenum –" bude mít typ `ELEMENT_TYPE_END` chyby kvůli problémům s načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé rozhraní identifikátory.</span><span class="sxs-lookup"><span data-stu-id="c03cf-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c03cf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c03cf-111">Requirements</span></span>  
 <span data-ttu-id="c03cf-112">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="c03cf-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c03cf-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c03cf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c03cf-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c03cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c03cf-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c03cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c03cf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c03cf-116">See also</span></span>

- [<span data-ttu-id="c03cf-117">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c03cf-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
