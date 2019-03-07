---
title: ICorDebugAppDomainEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fefc933cc84fede1f3dea16d4b13e09801a96e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497350"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="34a4f-102">ICorDebugAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="34a4f-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="34a4f-103">Zadaný počet domén aplikace získá z kolekce, spouští se na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="34a4f-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34a4f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34a4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34a4f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="34a4f-106">[in] Počet domén aplikace, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="34a4f-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="34a4f-107">[out] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugAppDomain, který představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="34a4f-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="34a4f-108">[out] Ukazatel na počet skutečně vrácených domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="34a4f-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="34a4f-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="34a4f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a4f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34a4f-110">Requirements</span></span>  
 <span data-ttu-id="34a4f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34a4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34a4f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34a4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34a4f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34a4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34a4f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34a4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
