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
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497969"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="9b046-102">ICorProfilerInfo::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9b046-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="9b046-103">Získá velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="9b046-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b046-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b046-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b046-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b046-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="9b046-106">pro ID objektu</span><span class="sxs-lookup"><span data-stu-id="9b046-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="9b046-107">mimo Ukazatel na velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9b046-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b046-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b046-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9b046-109">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9b046-109">This method is obsolete.</span></span> <span data-ttu-id="9b046-110">Vrátí COR_E_OVERFLOW pro objekty větší než 4GB na 64 platformách.</span><span class="sxs-lookup"><span data-stu-id="9b046-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="9b046-111">Místo toho použijte metodu [ICorProfilerInfo4:: getobjectsize2 –](icorprofilerinfo4-getobjectsize2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9b046-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="9b046-112">Různé objekty stejného typu mají často stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="9b046-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="9b046-113">Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="9b046-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="9b046-114">Velikost vrácená `GetObjectSize` metodou nezahrnuje žádné odsazení zarovnání, které se může zobrazit poté, co je objekt v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9b046-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="9b046-115">Pokud použijete `GetObjectSize` metodu pro přechod z objektu na objekt v haldě uvolňování paměti, podle potřeby přidejte odsazení zarovnání ručně.</span><span class="sxs-lookup"><span data-stu-id="9b046-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="9b046-116">Na 32 Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 a COR_PRF_GC_GEN_2 použít zarovnání na 4 bajty a COR_PRF_GC_LARGE_OBJECT_HEAP používá zarovnání na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9b046-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="9b046-117">V 64 bitových oknech je zarovnání vždy 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9b046-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b046-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b046-118">Requirements</span></span>  
 <span data-ttu-id="9b046-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b046-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b046-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9b046-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b046-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9b046-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b046-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b046-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b046-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b046-123">See also</span></span>

- [<span data-ttu-id="9b046-124">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b046-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
