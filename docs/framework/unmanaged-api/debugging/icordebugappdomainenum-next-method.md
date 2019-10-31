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
ms.openlocfilehash: 55e331ff4e6ada73dc92bb2e880f555887639714
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088795"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="78595-102">ICorDebugAppDomainEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="78595-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="78595-103">Načte zadaný počet aplikačních domén z kolekce počínaje aktuální pozicí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="78595-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78595-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78595-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78595-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78595-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="78595-106">pro Počet aplikačních domén, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="78595-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="78595-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugAppDomain, který představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="78595-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="78595-108">mimo Ukazatel na počet skutečně vrácených aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="78595-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="78595-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="78595-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78595-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78595-110">Requirements</span></span>  
 <span data-ttu-id="78595-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78595-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78595-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78595-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78595-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="78595-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78595-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78595-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
