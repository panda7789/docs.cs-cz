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
ms.openlocfilehash: c0c5dabd4145098941e9e8a7e36fa3215c26713d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084898"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="ded3d-102">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="ded3d-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="ded3d-103">Získá ukazatel [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instanci, která můžete vytvořit výčet objektů v sestavení se zadaným [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ded3d-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ded3d-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ded3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ded3d-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="ded3d-106">[out] Ukazatel na umístění v paměti, který obsahuje požadované `IAssemblyEnum` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="ded3d-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="ded3d-107">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ded3d-107">[in] Reserved for future extensibility.</span></span> `pUnkReserved` <span data-ttu-id="ded3d-108">musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ded3d-108">must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="ded3d-109">[in] `IAssemblyName` Požadovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="ded3d-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="ded3d-110">Tento název se používá k filtrování výčtu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="ded3d-111">Může mít hodnotu null pro všechna sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="ded3d-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ded3d-112">[in] Příznaky pro úpravu chování čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="ded3d-113">Tento parametr obsahuje přesně jeden bit z [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ded3d-114">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ded3d-114">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="ded3d-115">musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ded3d-115">must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded3d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ded3d-116">Remarks</span></span>  
 <span data-ttu-id="ded3d-117">`dwFlags` Parametr obsahuje přesně jeden bit z `ASM_CACHE_FLAGS` výčtu.</span><span class="sxs-lookup"><span data-stu-id="ded3d-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded3d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ded3d-118">Requirements</span></span>  
 <span data-ttu-id="ded3d-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded3d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded3d-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ded3d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ded3d-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ded3d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ded3d-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ded3d-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ded3d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ded3d-123">See also</span></span>

- [<span data-ttu-id="ded3d-124">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ded3d-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="ded3d-125">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ded3d-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="ded3d-126">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="ded3d-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
