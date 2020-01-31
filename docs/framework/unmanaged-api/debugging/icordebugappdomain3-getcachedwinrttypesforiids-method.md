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
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784893"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="dee6a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="dee6a-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="dee6a-103">Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dee6a-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dee6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dee6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dee6a-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="dee6a-106">pro Počet požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="dee6a-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="dee6a-107">pro Ukazatel na pole, které obsahuje identifikátory rozhraní odpovídající spravovaným reprezentacím typů prostředí Windows Runtime, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="dee6a-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="dee6a-108">mimo Ukazatel na adresu objektu rozhraní "ICorDebugTypeEnum", která umožňuje vyhodnotit výčet spravovaných reprezentace typů prostředí Windows Runtime uložených v mezipaměti, na základě identifikátorů rozhraní v `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="dee6a-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dee6a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dee6a-109">Remarks</span></span>  
 <span data-ttu-id="dee6a-110">Pokud metoda nepovede načíst informace pro konkrétní identifikátor rozhraní, odpovídající položka v kolekci "ICorDebugTypeEnum" bude mít typ `ELEMENT_TYPE_END` chyby z důvodu problémů načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé identifikátory rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dee6a-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee6a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dee6a-111">Requirements</span></span>  
 <span data-ttu-id="dee6a-112">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="dee6a-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="dee6a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dee6a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee6a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dee6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee6a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee6a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dee6a-116">See also</span></span>

- [<span data-ttu-id="dee6a-117">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dee6a-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
