---
title: ICorProfilerInfo::GetObjectSize – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ed27602dfa9090b46b842e4e65af8af373cc207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453906"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="00387-102">ICorProfilerInfo::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="00387-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="00387-103">Získá velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="00387-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00387-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00387-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00387-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00387-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="00387-106">[v] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="00387-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="00387-107">[out] Ukazatel na objektu velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="00387-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00387-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00387-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00387-109">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="00387-109">This method is obsolete.</span></span> <span data-ttu-id="00387-110">Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="00387-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="00387-111">Použití [icorprofilerinfo4::getobjectsize2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="00387-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="00387-112">Různé objekty stejné typy často mít stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="00387-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="00387-113">Některé typy, jako je například pole nebo řetězce, ale může mít různou velikost pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="00387-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="00387-114">Velikost vrácené `GetObjectSize` metoda neobsahuje žádné zarovnání odsazení, který se může zdát po objekt je v haldě kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="00387-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="00387-115">Pokud použijete `GetObjectSize` metoda pro přechod z objektu na objekt v haldě kolekce paměti přidat zarovnání odsazení ručně, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="00387-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="00387-116">V systému Windows 32-bit COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 používají 4bajtový zarovnání a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="00387-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="00387-117">Na 64bitovém systému Windows je zarovnání vždy 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="00387-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00387-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00387-118">Requirements</span></span>  
 <span data-ttu-id="00387-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00387-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00387-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00387-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00387-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00387-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00387-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00387-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00387-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="00387-123">See Also</span></span>  
 [<span data-ttu-id="00387-124">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00387-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
