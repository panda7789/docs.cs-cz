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
ms.openlocfilehash: 0e54027806cef07fad4740c3bf5226fd26c72570
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108779"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="ca509-102">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="ca509-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="ca509-103">Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která může vytvořit výčet objektů v sestavení pomocí zadaného [IAssemblyName](iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ca509-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca509-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca509-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca509-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca509-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="ca509-106">mimo Ukazatel na umístění v paměti, které obsahuje požadovaný ukazatel `IAssemblyEnum`.</span><span class="sxs-lookup"><span data-stu-id="ca509-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="ca509-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ca509-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ca509-108">`pUnkReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ca509-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="ca509-109">pro `IAssemblyName` požadovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca509-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="ca509-110">Tento název slouží k filtrování výčtu.</span><span class="sxs-lookup"><span data-stu-id="ca509-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="ca509-111">Aby bylo možné vytvořit výčet všech sestavení v globální mezipaměti sestavení (GAC), může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ca509-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ca509-112">pro Příznaky pro úpravu chování čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="ca509-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="ca509-113">Tento parametr obsahuje přesně jeden bit z výčtu [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ca509-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ca509-114">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ca509-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ca509-115">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ca509-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca509-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca509-116">Remarks</span></span>  
 <span data-ttu-id="ca509-117">Parametr `dwFlags` obsahuje přesně jeden bit z výčtu `ASM_CACHE_FLAGS`.</span><span class="sxs-lookup"><span data-stu-id="ca509-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca509-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca509-118">Requirements</span></span>  
 <span data-ttu-id="ca509-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca509-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca509-120">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ca509-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ca509-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca509-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca509-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca509-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca509-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca509-123">See also</span></span>

- [<span data-ttu-id="ca509-124">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca509-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="ca509-125">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca509-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="ca509-126">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="ca509-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
