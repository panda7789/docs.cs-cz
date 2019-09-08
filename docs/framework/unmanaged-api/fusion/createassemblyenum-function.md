---
title: CreateAssemblyEnum – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795386"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="05390-102">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="05390-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="05390-103">Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která může vytvořit výčet objektů v sestavení pomocí zadaného [IAssemblyName](iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="05390-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05390-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05390-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="05390-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05390-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="05390-106">mimo Ukazatel na umístění v paměti, které obsahuje požadovaný `IAssemblyEnum` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="05390-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="05390-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="05390-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="05390-108">`pUnkReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="05390-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="05390-109">pro `IAssemblyName` Z požadovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="05390-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="05390-110">Tento název slouží k filtrování výčtu.</span><span class="sxs-lookup"><span data-stu-id="05390-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="05390-111">Aby bylo možné vytvořit výčet všech sestavení v globální mezipaměti sestavení (GAC), může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="05390-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="05390-112">pro Příznaky pro úpravu chování čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="05390-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="05390-113">Tento parametr obsahuje přesně jeden bit z výčtu [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="05390-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="05390-114">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="05390-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="05390-115">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="05390-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05390-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05390-116">Remarks</span></span>  
 <span data-ttu-id="05390-117">Parametr obsahuje přesně jeden bit `ASM_CACHE_FLAGS` z výčtu. `dwFlags`</span><span class="sxs-lookup"><span data-stu-id="05390-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05390-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05390-118">Requirements</span></span>  
 <span data-ttu-id="05390-119">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05390-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05390-120">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="05390-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="05390-121">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05390-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05390-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05390-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05390-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05390-123">See also</span></span>

- [<span data-ttu-id="05390-124">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05390-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="05390-125">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05390-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="05390-126">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="05390-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
