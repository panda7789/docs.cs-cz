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
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870489"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="29c18-102">ICorProfilerInfo::GetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="29c18-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="29c18-103">Získá ukazatel na tělo metody v kódu jazyka MSIL (Microsoft Intermediate Language) od jejího záhlaví.</span><span class="sxs-lookup"><span data-stu-id="29c18-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29c18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29c18-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="29c18-106">pro ID modulu, ve kterém je funkce umístěna.</span><span class="sxs-lookup"><span data-stu-id="29c18-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="29c18-107">pro Token metadat pro metodu</span><span class="sxs-lookup"><span data-stu-id="29c18-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="29c18-108">mimo Ukazatel na záhlaví metody.</span><span class="sxs-lookup"><span data-stu-id="29c18-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="29c18-109">mimo Celé číslo, které určuje velikost metody.</span><span class="sxs-lookup"><span data-stu-id="29c18-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c18-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29c18-110">Remarks</span></span>  
 <span data-ttu-id="29c18-111">Metoda je vymezena modulem, ve kterém žije.</span><span class="sxs-lookup"><span data-stu-id="29c18-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="29c18-112">Vzhledem k tomu, že metoda `GetILFunctionBody` je navržena tak, aby před tím, než je načtena modulem CLR (Common Language Runtime), dala nástroji přístup k kódu jazyka MSIL, používá k nalezení požadované instance token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="29c18-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="29c18-113">`GetILFunctionBody` může vracet CORPROF_E_FUNCTION_NOT_IL HRESULT, pokud `methodId` odkazuje na metodu bez jakéhokoli kódu jazyka MSIL (jako je abstraktní metoda nebo metoda Invoke platformy (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="29c18-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c18-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29c18-114">Requirements</span></span>  
 <span data-ttu-id="29c18-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c18-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c18-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29c18-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29c18-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29c18-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c18-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c18-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c18-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29c18-119">See also</span></span>

- [<span data-ttu-id="29c18-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29c18-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
