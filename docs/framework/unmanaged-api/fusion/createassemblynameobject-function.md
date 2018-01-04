---
title: "CreateAssemblyNameObject – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyNameObject
helpviewer_keywords: CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d2616bd7aee878ebbc1d196cb1ac5f90ae7bd04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="d2239-102">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="d2239-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="d2239-103">Získá ukazatele rozhraní k [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="d2239-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2239-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2239-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2239-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2239-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="d2239-106">[out] Vrácený `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="d2239-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d2239-107">[v] Název sestavení, pro který chcete vytvořit nový `IAssemblyName` instance.</span><span class="sxs-lookup"><span data-stu-id="d2239-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d2239-108">[v] Příznaky, které mají být předána do konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="d2239-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d2239-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d2239-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d2239-110">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d2239-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2239-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2239-111">Requirements</span></span>  
 <span data-ttu-id="d2239-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2239-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2239-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d2239-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d2239-114">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2239-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2239-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2239-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2239-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2239-116">See Also</span></span>  
 [<span data-ttu-id="d2239-117">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2239-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="d2239-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="d2239-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
