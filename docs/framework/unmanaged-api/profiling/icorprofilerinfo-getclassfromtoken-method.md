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
ms.openlocfilehash: 12b4b897f9dc51175037d39c0368b6ce59fefefb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498476"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="7be90-102">ICorProfilerInfo::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7be90-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="7be90-103">Získá ID třídy s ohledem na token metadat.</span><span class="sxs-lookup"><span data-stu-id="7be90-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="7be90-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7be90-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7be90-105">Místo toho použijte [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs –](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7be90-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be90-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7be90-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be90-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be90-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="7be90-108">pro ID modulu, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="7be90-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="7be90-109">pro `mdTypeDef`Token metadat, který odkazuje na třídu.</span><span class="sxs-lookup"><span data-stu-id="7be90-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="7be90-110">mimo Ukazatel na ID třídy.</span><span class="sxs-lookup"><span data-stu-id="7be90-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7be90-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7be90-111">Remarks</span></span>  
 <span data-ttu-id="7be90-112">Tato metoda je zastaralá; místo toho použijte `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="7be90-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be90-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7be90-113">Requirements</span></span>  
 <span data-ttu-id="7be90-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be90-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be90-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7be90-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7be90-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7be90-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7be90-117">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="7be90-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be90-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7be90-118">See also</span></span>

- [<span data-ttu-id="7be90-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7be90-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
