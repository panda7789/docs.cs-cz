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
ms.openlocfilehash: 12524de994264d83abf5b5338654e89a0964adff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667697"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="bcc73-102">ICorProfilerInfo::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="bcc73-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="bcc73-103">Získá ID třídy, zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="bcc73-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="bcc73-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="bcc73-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bcc73-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span><span class="sxs-lookup"><span data-stu-id="bcc73-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc73-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcc73-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcc73-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcc73-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="bcc73-108">[in] ID modulu, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="bcc73-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="bcc73-109">[in] `mdTypeDef` Token metadat, který odkazuje na třídu.</span><span class="sxs-lookup"><span data-stu-id="bcc73-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="bcc73-110">[out] Ukazatel na ID třídy.</span><span class="sxs-lookup"><span data-stu-id="bcc73-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcc73-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcc73-111">Remarks</span></span>  
 <span data-ttu-id="bcc73-112">Tato metoda je zastaralá; Místo toho použijte `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="bcc73-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcc73-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcc73-113">Requirements</span></span>  
 <span data-ttu-id="bcc73-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcc73-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcc73-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bcc73-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcc73-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcc73-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcc73-117">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="bcc73-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc73-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcc73-118">See also</span></span>
- [<span data-ttu-id="bcc73-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcc73-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
