---
title: "ICorProfilerInfo::GetILFunctionBody – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 035c2a1926d80b4aaea57523b4ecdd3da6873efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="ae5bf-102">ICorProfilerInfo::GetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="ae5bf-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="ae5bf-103">Získá ukazatel k tělu metody v kódu (MSIL intermediate language) společnosti Microsoft, začínající na jeho záhlaví.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae5bf-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae5bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae5bf-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ae5bf-106">[v] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="ae5bf-107">[v] Token metadata pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="ae5bf-108">[out] Ukazatel na záhlaví metody.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="ae5bf-109">[out] Celé číslo, které určuje velikost metody.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae5bf-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae5bf-110">Remarks</span></span>  
 <span data-ttu-id="ae5bf-111">Metoda je vymezen modulu, ve kterém je umístěn.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="ae5bf-112">Protože `GetILFunctionBody` metoda je navržená tak, aby poskytl přístup k nástroji kód MSIL předtím, než byl načten modulem common language runtime (CLR), použije token metadata metody najít požadované instance.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="ae5bf-113">`GetILFunctionBody`CORPROF_E_FUNCTION_NOT_IL HRESULT může vrátit, pokud `methodId` odkazuje na metodu, bez jakékoli MSIL kód (například abstraktní metodu nebo platformu invoke – metoda (PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="ae5bf-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5bf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae5bf-114">Requirements</span></span>  
 <span data-ttu-id="ae5bf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae5bf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5bf-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae5bf-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae5bf-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae5bf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae5bf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5bf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae5bf-119">See Also</span></span>  
 [<span data-ttu-id="ae5bf-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae5bf-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
