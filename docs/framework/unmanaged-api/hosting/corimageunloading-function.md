---
title: _CorImageUnloading – funkce
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b488b6a887b0c66d8c17f8ea78f48f7d2ea31011
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758406"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="c97bc-102">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="c97bc-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="c97bc-103">Upozorní zavaděč na bitové kopie spravovaného modulu jsou uvolněna.</span><span class="sxs-lookup"><span data-stu-id="c97bc-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="c97bc-104">Tato funkce není implementována.</span><span class="sxs-lookup"><span data-stu-id="c97bc-104">This function is not implemented.</span></span> <span data-ttu-id="c97bc-105">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c97bc-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c97bc-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c97bc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c97bc-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="c97bc-108">[in] Ukazatel na počáteční umístění image uvolnit.</span><span class="sxs-lookup"><span data-stu-id="c97bc-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97bc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c97bc-109">Requirements</span></span>  
 <span data-ttu-id="c97bc-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97bc-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c97bc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c97bc-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c97bc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c97bc-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97bc-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c97bc-114">See also</span></span>

- [<span data-ttu-id="c97bc-115">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c97bc-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
