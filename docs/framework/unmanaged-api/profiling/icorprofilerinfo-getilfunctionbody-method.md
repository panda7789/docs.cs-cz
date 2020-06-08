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
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503000"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="eb5de-102">ICorProfilerInfo::GetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="eb5de-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="eb5de-103">Získá ukazatel na tělo metody v kódu jazyka MSIL (Microsoft Intermediate Language) od jejího záhlaví.</span><span class="sxs-lookup"><span data-stu-id="eb5de-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb5de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb5de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb5de-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="eb5de-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="eb5de-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="eb5de-107">pro Token metadat pro metodu</span><span class="sxs-lookup"><span data-stu-id="eb5de-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="eb5de-108">mimo Ukazatel na záhlaví metody.</span><span class="sxs-lookup"><span data-stu-id="eb5de-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="eb5de-109">mimo Celé číslo, které určuje velikost metody.</span><span class="sxs-lookup"><span data-stu-id="eb5de-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb5de-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb5de-110">Remarks</span></span>  
 <span data-ttu-id="eb5de-111">Metoda je vymezena modulem, ve kterém žije.</span><span class="sxs-lookup"><span data-stu-id="eb5de-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="eb5de-112">Vzhledem k tomu, že `GetILFunctionBody` Metoda je navržena tak, aby před tím, než je načtena modulem CLR (Common Language Runtime), dala nástroji přístup k kódu jazyka MSIL, používá k nalezení požadované instance token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="eb5de-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="eb5de-113">`GetILFunctionBody`může vrátit CORPROF_E_FUNCTION_NOT_IL HRESULT `methodId` , pokud odkazuje na metodu bez jakéhokoli kódu jazyka MSIL (jako je abstraktní metoda nebo metoda Invoke platformy (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="eb5de-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb5de-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb5de-114">Requirements</span></span>  
 <span data-ttu-id="eb5de-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb5de-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb5de-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb5de-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb5de-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eb5de-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb5de-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb5de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb5de-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb5de-119">See also</span></span>

- [<span data-ttu-id="eb5de-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb5de-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
