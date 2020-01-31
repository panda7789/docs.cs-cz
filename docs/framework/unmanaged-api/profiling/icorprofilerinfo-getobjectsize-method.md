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
ms.openlocfilehash: b860cf6eb07c3f063e3e51514f8492cf4af9e8ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869669"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="6eec7-102">ICorProfilerInfo::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6eec7-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="6eec7-103">Získá velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="6eec7-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eec7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eec7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eec7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eec7-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="6eec7-106">pro ID objektu</span><span class="sxs-lookup"><span data-stu-id="6eec7-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="6eec7-107">mimo Ukazatel na velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6eec7-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eec7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eec7-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6eec7-109">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6eec7-109">This method is obsolete.</span></span> <span data-ttu-id="6eec7-110">Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64 platformách.</span><span class="sxs-lookup"><span data-stu-id="6eec7-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="6eec7-111">Místo toho použijte metodu [ICorProfilerInfo4:: getobjectsize2 –](icorprofilerinfo4-getobjectsize2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6eec7-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="6eec7-112">Různé objekty stejného typu mají často stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="6eec7-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="6eec7-113">Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="6eec7-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="6eec7-114">Velikost vrácená metodou `GetObjectSize` neobsahuje žádné odsazení zarovnání, které se může zobrazit poté, co je objekt v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6eec7-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="6eec7-115">Použijete-li metodu `GetObjectSize` k přechodu z objektu na objekt v haldě uvolňování paměti, podle potřeby přidejte odsazení zarovnání ručně.</span><span class="sxs-lookup"><span data-stu-id="6eec7-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="6eec7-116">Na 32 Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 použít zarovnání na 4 bajty a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="6eec7-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="6eec7-117">V 64 bitových oknech je zarovnání vždy 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="6eec7-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eec7-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eec7-118">Requirements</span></span>  
 <span data-ttu-id="6eec7-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eec7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eec7-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6eec7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6eec7-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6eec7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eec7-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eec7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eec7-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eec7-123">See also</span></span>

- [<span data-ttu-id="6eec7-124">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eec7-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
