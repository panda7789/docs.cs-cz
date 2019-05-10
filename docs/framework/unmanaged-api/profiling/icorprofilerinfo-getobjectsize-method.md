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
ms.openlocfilehash: fb69670d06230c06f1ffc2793b6fa9d45191ca77
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606526"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="f9d31-102">ICorProfilerInfo::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f9d31-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="f9d31-103">Získá velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="f9d31-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9d31-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9d31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9d31-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f9d31-106">[in] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="f9d31-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f9d31-107">[out] Ukazatel objekt velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f9d31-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9d31-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9d31-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f9d31-109">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f9d31-109">This method is obsolete.</span></span> <span data-ttu-id="f9d31-110">Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="f9d31-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="f9d31-111">Použití [icorprofilerinfo4::getobjectsize2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="f9d31-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="f9d31-112">Různé objekty stejné typy často mají stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="f9d31-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="f9d31-113">Některé typy, například pole nebo řetězce, ale může mít jinou velikost pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="f9d31-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="f9d31-114">Velikost vrácené `GetObjectSize` způsob neobsahuje žádné zarovnání odsazení, který se může zdát, jakmile je objekt na haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f9d31-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="f9d31-115">Pokud používáte `GetObjectSize` metoda pro přechod z objektu na haldě uvolňování paměti kolekce přidat zarovnání odsazení ručně, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f9d31-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="f9d31-116">Na Windows 32-bit COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 používat 4bajtové zarovnání a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f9d31-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="f9d31-117">Na Windows 64-bit zarovnání je vždy 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f9d31-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d31-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9d31-118">Requirements</span></span>  
 <span data-ttu-id="f9d31-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9d31-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d31-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9d31-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9d31-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9d31-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9d31-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d31-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d31-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9d31-123">See also</span></span>

- [<span data-ttu-id="f9d31-124">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9d31-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
