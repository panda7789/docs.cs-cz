---
title: ICorProfilerObjectEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 99778240afb7e296b93cd87ab91feeca20d02637
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428276"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="e8b84-102">ICorProfilerObjectEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="e8b84-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="e8b84-103">Získá ukazatel rozhraní na kopii tohoto rozhraní [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e8b84-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8b84-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8b84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8b84-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e8b84-106">mimo Ukazatel na ukazatel rozhraní, který ukazuje na kopii tohoto `ICorProfilerObjectEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e8b84-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="e8b84-107">Kopie udržuje svůj vlastní stav výčtu odděleně od tohoto.</span><span class="sxs-lookup"><span data-stu-id="e8b84-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="e8b84-108">Počáteční pozice kurzoru pro kopii ale bude stejná jako aktuální pozice kurzoru tohoto čítače.</span><span class="sxs-lookup"><span data-stu-id="e8b84-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8b84-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8b84-109">Requirements</span></span>  
 <span data-ttu-id="e8b84-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8b84-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b84-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e8b84-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8b84-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8b84-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8b84-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b84-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b84-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8b84-114">See also</span></span>

- [<span data-ttu-id="e8b84-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8b84-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
