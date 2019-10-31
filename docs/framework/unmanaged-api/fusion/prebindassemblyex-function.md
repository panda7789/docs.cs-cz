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
ms.openlocfilehash: db3ba3380d1fc30a8f34683618b5cc326d7d1906
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123061"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="4279e-102">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="4279e-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="4279e-103">Načte zobrazovaný název po zásadě pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="4279e-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="4279e-104">Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="4279e-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4279e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4279e-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4279e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4279e-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="4279e-107">pro Identifikuje kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="4279e-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="4279e-108">pro Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="4279e-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="4279e-109">pro Identifikuje nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="4279e-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="4279e-110">Tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="4279e-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="4279e-111">pro Určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4279e-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="4279e-112">mimo Obsahuje zobrazovaný název po zásadě.</span><span class="sxs-lookup"><span data-stu-id="4279e-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4279e-113">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4279e-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4279e-114">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4279e-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4279e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4279e-115">Remarks</span></span>  
 <span data-ttu-id="4279e-116">Výstupní parametr `ppNamePostPolicy` je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="4279e-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="4279e-117">V opačném případě má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4279e-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4279e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4279e-118">Requirements</span></span>  
 <span data-ttu-id="4279e-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4279e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4279e-120">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4279e-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4279e-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4279e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4279e-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4279e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4279e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4279e-123">See also</span></span>

- [<span data-ttu-id="4279e-124">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="4279e-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
