---
title: PreBindAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d3e2535851d39be642de56a86b78c328ecaf446
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431998"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="f33bb-102">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="f33bb-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="f33bb-103">Získá po zásady zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f33bb-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="f33bb-104">Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="f33bb-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f33bb-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f33bb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f33bb-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="f33bb-107">[v] Identifikuje kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="f33bb-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="f33bb-108">[v] Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f33bb-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="f33bb-109">[v] Určuje nadřazený sestavení.</span><span class="sxs-lookup"><span data-stu-id="f33bb-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="f33bb-110">Tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="f33bb-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="f33bb-111">[v] Určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f33bb-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="f33bb-112">[out] Obsahuje po zásady zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="f33bb-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f33bb-113">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f33bb-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f33bb-114">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="f33bb-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f33bb-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f33bb-115">Remarks</span></span>  
 <span data-ttu-id="f33bb-116">`ppNamePostPolicy` Výstupní parametr je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="f33bb-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="f33bb-117">Jinak má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f33bb-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f33bb-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f33bb-118">Requirements</span></span>  
 <span data-ttu-id="f33bb-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f33bb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f33bb-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f33bb-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f33bb-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f33bb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f33bb-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33bb-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f33bb-123">See Also</span></span>  
 [<span data-ttu-id="f33bb-124">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="f33bb-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
