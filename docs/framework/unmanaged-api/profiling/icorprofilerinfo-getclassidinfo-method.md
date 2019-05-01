---
title: ICorProfilerInfo::GetClassIDInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45abb39fa7266e19bbd375b476f2ab48bfc5914d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041324"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="b0e42-102">ICorProfilerInfo::GetClassIDInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="b0e42-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="b0e42-103">Získá nadřazený modulu a tokenem metadat pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="b0e42-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0e42-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0e42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0e42-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b0e42-106">[in] ID třídy, pro které chcete získat informace o.</span><span class="sxs-lookup"><span data-stu-id="b0e42-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b0e42-107">[out] Ukazatel na ID modulu nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="b0e42-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="b0e42-108">[out] Ukazatel na token metadat pro třídu.</span><span class="sxs-lookup"><span data-stu-id="b0e42-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0e42-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0e42-109">Remarks</span></span>  
 <span data-ttu-id="b0e42-110">Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získání metadat rozhraní pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="b0e42-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="b0e42-111">Token metadat, který je vrácen do umístění odkazuje `pTypeDefToken` lze použít k přístupu k metadatům pro třídu.</span><span class="sxs-lookup"><span data-stu-id="b0e42-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="b0e42-112">Chcete-li získat další informace pro obecné typy, použijte [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="b0e42-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e42-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0e42-113">Requirements</span></span>  
 <span data-ttu-id="b0e42-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e42-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e42-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0e42-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0e42-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e42-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e42-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e42-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e42-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0e42-118">See also</span></span>

- [<span data-ttu-id="b0e42-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0e42-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
