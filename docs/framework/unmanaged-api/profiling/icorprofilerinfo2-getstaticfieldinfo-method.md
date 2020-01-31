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
ms.openlocfilehash: d30d0bc262d76cf8980f90d8384173d89baf92d5
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862682"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="99938-102">ICorProfilerInfo2::GetStaticFieldInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="99938-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="99938-103">Získá hodnotu, která označuje druh statického typu, který se vztahuje k určenému poli.</span><span class="sxs-lookup"><span data-stu-id="99938-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99938-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99938-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99938-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99938-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="99938-106">pro ID třídy, ve které je definováno statické pole.</span><span class="sxs-lookup"><span data-stu-id="99938-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="99938-107">pro Token metadat pro statické pole</span><span class="sxs-lookup"><span data-stu-id="99938-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="99938-108">mimo Ukazatel na hodnotu výčtu [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) , která označuje, zda je zadané pole statické, a pokud ano, druh statického, který se vztahuje k poli.</span><span class="sxs-lookup"><span data-stu-id="99938-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99938-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99938-109">Remarks</span></span>  
 <span data-ttu-id="99938-110">Tyto informace lze použít k určení, která funkce má být volána, aby získala adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="99938-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="99938-111">Kód profileru by měl stále kontrolovat metadata pro statické pole, aby se zajistilo, že má ve skutečnosti adresu.</span><span class="sxs-lookup"><span data-stu-id="99938-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="99938-112">Statické literály (tj. konstanty) existují pouze v metadatech a nemají adresu.</span><span class="sxs-lookup"><span data-stu-id="99938-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99938-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99938-113">Requirements</span></span>  
 <span data-ttu-id="99938-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99938-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99938-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="99938-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99938-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99938-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99938-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99938-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99938-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99938-118">See also</span></span>

- [<span data-ttu-id="99938-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99938-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="99938-120">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99938-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
