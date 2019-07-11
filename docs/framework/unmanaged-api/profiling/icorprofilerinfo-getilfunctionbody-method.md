---
title: ICorProfilerInfo::GetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 484fb5b8398e3ebd61d1c300afec1536ee1dc0c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780600"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="dc925-102">ICorProfilerInfo::GetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="dc925-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="dc925-103">Získá ukazatel do těla metody v kódu Microsoft intermediate language (MSIL) začínající na jeho záhlaví.</span><span class="sxs-lookup"><span data-stu-id="dc925-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc925-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc925-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc925-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc925-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="dc925-106">[in] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="dc925-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="dc925-107">[in] Token metadat pro metodu.</span><span class="sxs-lookup"><span data-stu-id="dc925-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="dc925-108">[out] Ukazatel na záhlaví metody.</span><span class="sxs-lookup"><span data-stu-id="dc925-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="dc925-109">[out] Celé číslo, které určuje velikost metody.</span><span class="sxs-lookup"><span data-stu-id="dc925-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc925-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc925-110">Remarks</span></span>  
 <span data-ttu-id="dc925-111">Metoda je určeno v modulu, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="dc925-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="dc925-112">Vzhledem k tomu, `GetILFunctionBody` metoda je určena poskytnout přístup k nástroji pro kód jazyka MSIL, předtím, než byl načten modulem common language runtime (CLR), použije token metadat metody k vyhledání požadovaného instance.</span><span class="sxs-lookup"><span data-stu-id="dc925-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="dc925-113">`GetILFunctionBody` může vrátit hodnotu HRESULT CORPROF_E_FUNCTION_NOT_IL, pokud `methodId` odkazuje na metodu, bez jakékoli MSIL kód (jako abstraktní metody nebo platformu vyvolání metody (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="dc925-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc925-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc925-114">Requirements</span></span>  
 <span data-ttu-id="dc925-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc925-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc925-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc925-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc925-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc925-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc925-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc925-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc925-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc925-119">See also</span></span>

- [<span data-ttu-id="dc925-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc925-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
