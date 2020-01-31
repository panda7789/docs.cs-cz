---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength – metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: a675cc301d2dd32f87e3864a3123e2044761ef91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868353"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="3c123-102">ICorProfilerInfo7:: GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="3c123-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="3c123-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3c123-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3c123-104">Vrátí délku datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="3c123-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c123-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c123-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c123-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c123-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3c123-107">pro Identifikátor modulu, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="3c123-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="3c123-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="3c123-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="3c123-109">mimo Ukazatel na hodnotu `DWORD`, která při návratu metody obsahuje délku datového proudu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3c123-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c123-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3c123-110">Return Value</span></span>  
 <span data-ttu-id="3c123-111">Metoda vrátí `S_OK`, pokud je možné určit délku paměťového proudu, i když je nula (0).</span><span class="sxs-lookup"><span data-stu-id="3c123-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="3c123-112">Metoda vrací `CORPROF_E_MODULE_IS_DYNAMIC`, pokud byla metoda vytvořena pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3c123-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c123-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c123-113">Remarks</span></span>  
 <span data-ttu-id="3c123-114">Pokud má modul symboly v paměti, je délka datového proudu umístěna v `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="3c123-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="3c123-115">Pokud modul neobsahuje symboly v paměti, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="3c123-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c123-116">Aktuální implementace nepodporuje reflexe. Emit.</span><span class="sxs-lookup"><span data-stu-id="3c123-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="3c123-117">Pokud byl modul vytvořen pomocí reflexe. Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="3c123-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c123-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c123-118">Requirements</span></span>  
 <span data-ttu-id="3c123-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c123-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c123-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3c123-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c123-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3c123-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c123-122">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c123-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c123-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c123-123">See also</span></span>

- [<span data-ttu-id="3c123-124">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c123-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
