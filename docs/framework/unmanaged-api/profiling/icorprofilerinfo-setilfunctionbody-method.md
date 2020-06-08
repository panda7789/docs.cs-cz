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
ms.openlocfilehash: 462fc7222243f8cad4e1d03d1717eedace549836
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502935"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="d4aaf-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="d4aaf-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="d4aaf-103">Nahradí tělo zadané funkce v zadaném modulu.</span><span class="sxs-lookup"><span data-stu-id="d4aaf-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4aaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4aaf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4aaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4aaf-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d4aaf-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="d4aaf-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="d4aaf-107">pro Token funkce, pro kterou má být nahrazena tělo</span><span class="sxs-lookup"><span data-stu-id="d4aaf-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="d4aaf-108">pro Nové záhlaví funkce</span><span class="sxs-lookup"><span data-stu-id="d4aaf-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4aaf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4aaf-109">Remarks</span></span>  
 <span data-ttu-id="d4aaf-110">`SetILFunctionBody`Metoda nahradí relativní virtuální adresu funkce v metadatech tak, aby odkazovala na nový text funkce, a podle potřeby upraví všechny interní datové struktury.</span><span class="sxs-lookup"><span data-stu-id="d4aaf-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="d4aaf-111">`SetILFunctionBody`Metodu lze volat pouze pro funkce, které nebyly nikdy zkompilovány kompilátorem JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="d4aaf-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="d4aaf-112">Pomocí metody [ICorProfilerInfo:: GetILFunctionBodyAllocator –](icorprofilerinfo-getilfunctionbodyallocator-method.md) přidělte místo pro novou metodu, aby byla zajištěna kompatibilita vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d4aaf-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4aaf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4aaf-113">Requirements</span></span>  
 <span data-ttu-id="d4aaf-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4aaf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4aaf-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d4aaf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4aaf-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4aaf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4aaf-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4aaf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4aaf-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4aaf-118">See also</span></span>

- [<span data-ttu-id="d4aaf-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4aaf-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
