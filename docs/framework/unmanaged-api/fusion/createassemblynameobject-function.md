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
ms.openlocfilehash: 8281c7944ff96110145a6f5c43a0a0e7da58fdcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="e2c78-102">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="e2c78-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="e2c78-103">Získá ukazatele rozhraní k [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="e2c78-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2c78-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2c78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2c78-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="e2c78-106">[out] Vrácený `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="e2c78-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="e2c78-107">[v] Název sestavení, pro který chcete vytvořit nový `IAssemblyName` instance.</span><span class="sxs-lookup"><span data-stu-id="e2c78-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e2c78-108">[v] Příznaky, které mají být předána do konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="e2c78-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e2c78-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e2c78-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e2c78-110">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="e2c78-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c78-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2c78-111">Requirements</span></span>  
 <span data-ttu-id="e2c78-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2c78-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c78-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e2c78-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e2c78-114">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2c78-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2c78-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c78-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2c78-116">See Also</span></span>  
 [<span data-ttu-id="e2c78-117">Iassemblyname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2c78-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="e2c78-118">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="e2c78-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
