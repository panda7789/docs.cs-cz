---
title: ICorProfilerInfo::GetClassFromToken – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 335c25316b34f79b8d02eea5a7dd4ed7994fc754
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780181"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="acd0e-102">ICorProfilerInfo::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="acd0e-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="acd0e-103">Získá ID třídy, zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="acd0e-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="acd0e-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="acd0e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="acd0e-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span><span class="sxs-lookup"><span data-stu-id="acd0e-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd0e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acd0e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acd0e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="acd0e-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="acd0e-108">[in] ID modulu, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="acd0e-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="acd0e-109">[in] `mdTypeDef` Token metadat, který odkazuje na třídu.</span><span class="sxs-lookup"><span data-stu-id="acd0e-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="acd0e-110">[out] Ukazatel na ID třídy.</span><span class="sxs-lookup"><span data-stu-id="acd0e-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acd0e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acd0e-111">Remarks</span></span>  
 <span data-ttu-id="acd0e-112">Tato metoda je zastaralá; Místo toho použijte `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="acd0e-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd0e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acd0e-113">Requirements</span></span>  
 <span data-ttu-id="acd0e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acd0e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd0e-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="acd0e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="acd0e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acd0e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acd0e-117">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="acd0e-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd0e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acd0e-118">See also</span></span>

- [<span data-ttu-id="acd0e-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acd0e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
