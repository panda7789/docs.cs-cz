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
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863950"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="97806-102">ICorProfilerInfo::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="97806-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="97806-103">Získá ID třídy s ohledem na token metadat.</span><span class="sxs-lookup"><span data-stu-id="97806-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="97806-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="97806-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="97806-105">Místo toho použijte [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs –](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="97806-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97806-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97806-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97806-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="97806-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="97806-108">pro ID modulu, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="97806-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="97806-109">pro Token metadat `mdTypeDef`, který odkazuje na třídu.</span><span class="sxs-lookup"><span data-stu-id="97806-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="97806-110">mimo Ukazatel na ID třídy.</span><span class="sxs-lookup"><span data-stu-id="97806-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97806-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97806-111">Remarks</span></span>  
 <span data-ttu-id="97806-112">Tato metoda je zastaralá; místo toho použijte `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="97806-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97806-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97806-113">Requirements</span></span>  
 <span data-ttu-id="97806-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97806-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97806-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="97806-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97806-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97806-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97806-117">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="97806-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97806-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97806-118">See also</span></span>

- [<span data-ttu-id="97806-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97806-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
