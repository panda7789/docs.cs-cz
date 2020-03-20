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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179065"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="f978c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="f978c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="f978c-103">Získá čítač výčtu pro typy prostředí Windows Runtime uložené v mezipaměti v doméně aplikace na základě jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f978c-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f978c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f978c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f978c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f978c-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="f978c-106">[v] Počet požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="f978c-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="f978c-107">[v] Ukazatel na pole, které obsahuje identifikátory rozhraní odpovídající spravovaným reprezentacím typů prostředí Windows Runtime, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f978c-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="f978c-108">[out] Ukazatel na adresu objektu rozhraní ICorDebugTypeEnum, který umožňuje výčet spravovaných reprezentací načtených v prostředí Windows Runtime v mezipaměti na základě identifikátorů rozhraní v `iidsToResolve`aplikaci .</span><span class="sxs-lookup"><span data-stu-id="f978c-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f978c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f978c-109">Remarks</span></span>  
 <span data-ttu-id="f978c-110">Pokud se metodě nepodaří načíst informace pro konkrétní identifikátor rozhraní, odpovídající položka v kolekci `ELEMENT_TYPE_END` "ICorDebugTypeEnum" `ELEMENT_TYPE_VOID` bude mít typ chyb z důvodu problémů s načítáním dat nebo pro neznámé identifikátory rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f978c-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f978c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f978c-111">Requirements</span></span>  
 <span data-ttu-id="f978c-112">**Platformy:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="f978c-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="f978c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f978c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f978c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f978c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f978c-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f978c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f978c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f978c-116">See also</span></span>

- [<span data-ttu-id="f978c-117">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f978c-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
