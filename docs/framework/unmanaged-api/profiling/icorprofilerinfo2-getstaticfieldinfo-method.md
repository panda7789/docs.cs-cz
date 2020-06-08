---
title: ICorProfilerInfo2::GetStaticFieldInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e1dd6addd9053ffb6cf2ce23408673d8fca17cb5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496838"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="935b9-102">ICorProfilerInfo2::GetStaticFieldInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="935b9-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="935b9-103">Získá hodnotu, která označuje druh statického typu, který se vztahuje k určenému poli.</span><span class="sxs-lookup"><span data-stu-id="935b9-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="935b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="935b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="935b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="935b9-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="935b9-106">pro ID třídy, ve které je definováno statické pole.</span><span class="sxs-lookup"><span data-stu-id="935b9-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="935b9-107">pro Token metadat pro statické pole</span><span class="sxs-lookup"><span data-stu-id="935b9-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="935b9-108">mimo Ukazatel na hodnotu výčtu [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) , která označuje, zda je zadané pole statické, a pokud ano, druh statického, který se vztahuje k poli.</span><span class="sxs-lookup"><span data-stu-id="935b9-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="935b9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="935b9-109">Remarks</span></span>  
 <span data-ttu-id="935b9-110">Tyto informace lze použít k určení, která funkce má být volána, aby získala adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="935b9-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="935b9-111">Kód profileru by měl stále kontrolovat metadata pro statické pole, aby se zajistilo, že má ve skutečnosti adresu.</span><span class="sxs-lookup"><span data-stu-id="935b9-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="935b9-112">Statické literály (tj. konstanty) existují pouze v metadatech a nemají adresu.</span><span class="sxs-lookup"><span data-stu-id="935b9-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="935b9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="935b9-113">Requirements</span></span>  
 <span data-ttu-id="935b9-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="935b9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="935b9-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="935b9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="935b9-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="935b9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="935b9-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="935b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="935b9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="935b9-118">See also</span></span>

- [<span data-ttu-id="935b9-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="935b9-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="935b9-120">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="935b9-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
