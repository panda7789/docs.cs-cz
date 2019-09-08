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
ms.openlocfilehash: 8aa2d174200db76f5c7a6db43e14bb6904604226
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796337"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="4c537-102">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="4c537-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="4c537-103">Načte zobrazovaný název po zásadě pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c537-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="4c537-104">Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="4c537-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c537-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c537-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4c537-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c537-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="4c537-107">pro Identifikuje kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c537-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="4c537-108">pro Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c537-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="4c537-109">pro Identifikuje nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c537-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="4c537-110">Tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="4c537-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="4c537-111">pro Určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4c537-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="4c537-112">mimo Obsahuje zobrazovaný název po zásadě.</span><span class="sxs-lookup"><span data-stu-id="4c537-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4c537-113">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4c537-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4c537-114">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4c537-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c537-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c537-115">Remarks</span></span>  
 <span data-ttu-id="4c537-116">`ppNamePostPolicy` Výstupní parametr je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="4c537-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="4c537-117">V opačném případě má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4c537-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c537-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c537-118">Requirements</span></span>  
 <span data-ttu-id="4c537-119">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c537-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c537-120">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4c537-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4c537-121">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c537-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c537-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c537-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c537-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c537-123">See also</span></span>

- [<span data-ttu-id="4c537-124">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="4c537-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
