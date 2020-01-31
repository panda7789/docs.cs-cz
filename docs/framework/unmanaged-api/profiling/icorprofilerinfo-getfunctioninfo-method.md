---
title: ICorProfilerInfo::GetFunctionInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863618"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="0d45a-102">ICorProfilerInfo::GetFunctionInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="0d45a-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="0d45a-103">Získá nadřazenou třídu a token metadat pro určenou funkci.</span><span class="sxs-lookup"><span data-stu-id="0d45a-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d45a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d45a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d45a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d45a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0d45a-106">pro ID funkce, pro kterou se má získat nadřazená třída a token metadat</span><span class="sxs-lookup"><span data-stu-id="0d45a-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="0d45a-107">mimo Ukazatel na nadřazenou třídu funkce.</span><span class="sxs-lookup"><span data-stu-id="0d45a-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0d45a-108">mimo Ukazatel na modul, ve kterém je definována nadřazená třída funkce.</span><span class="sxs-lookup"><span data-stu-id="0d45a-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="0d45a-109">mimo Ukazatel na token metadat pro funkci.</span><span class="sxs-lookup"><span data-stu-id="0d45a-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d45a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d45a-110">Remarks</span></span>  
 <span data-ttu-id="0d45a-111">Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní metadat pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="0d45a-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="0d45a-112">Token metadat, který je vrácen do umístění odkazovaného `pToken` lze následně použít pro přístup k metadatům funkce.</span><span class="sxs-lookup"><span data-stu-id="0d45a-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="0d45a-113">`ClassID` funkce na obecné třídě nemusí být získatelné bez dalších kontextových informací o použití funkce.</span><span class="sxs-lookup"><span data-stu-id="0d45a-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="0d45a-114">V takovém případě bude `pClassId` 0.</span><span class="sxs-lookup"><span data-stu-id="0d45a-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="0d45a-115">Kód profileru by měl používat [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou COR_PRF_FRAME_INFO k poskytnutí více kontextu.</span><span class="sxs-lookup"><span data-stu-id="0d45a-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d45a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d45a-116">Requirements</span></span>  
 <span data-ttu-id="0d45a-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d45a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d45a-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d45a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d45a-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d45a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d45a-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d45a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d45a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d45a-121">See also</span></span>

- [<span data-ttu-id="0d45a-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d45a-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
