---
title: ICorProfilerInfo::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: da81bd3e255898543c94d4ac64c6afbf39b6bdba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449883"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="f2942-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="f2942-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="f2942-103">Nahradí tělo zadané funkce v zadaném modulu.</span><span class="sxs-lookup"><span data-stu-id="f2942-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2942-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2942-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2942-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2942-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f2942-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="f2942-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="f2942-107">pro Token funkce, pro kterou má být nahrazena tělo</span><span class="sxs-lookup"><span data-stu-id="f2942-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="f2942-108">pro Nové záhlaví funkce</span><span class="sxs-lookup"><span data-stu-id="f2942-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2942-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2942-109">Remarks</span></span>  
 <span data-ttu-id="f2942-110">Metoda `SetILFunctionBody` nahradí relativní virtuální adresu funkce v metadatech tak, aby odkazovala na nový text funkce, a podle potřeby upraví všechny interní datové struktury.</span><span class="sxs-lookup"><span data-stu-id="f2942-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="f2942-111">Metodu `SetILFunctionBody` lze volat pouze pro funkce, které nebyly nikdy zkompilovány kompilátorem JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="f2942-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="f2942-112">Pomocí metody [ICorProfilerInfo:: GetILFunctionBodyAllocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) přidělte místo pro novou metodu, aby byla zajištěna kompatibilita vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f2942-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2942-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2942-113">Requirements</span></span>  
 <span data-ttu-id="f2942-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2942-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2942-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2942-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2942-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f2942-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2942-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2942-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2942-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2942-118">See also</span></span>

- [<span data-ttu-id="f2942-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2942-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
