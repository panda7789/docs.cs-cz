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
ms.openlocfilehash: be2edd5b217466a58aa9c478dadc10004ebda721
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556139"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="41aa4-102">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="41aa4-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="41aa4-103">Upozorní zavaděč na bitové kopie spravovaného modulu jsou uvolněna.</span><span class="sxs-lookup"><span data-stu-id="41aa4-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="41aa4-104">Tato funkce není implementována.</span><span class="sxs-lookup"><span data-stu-id="41aa4-104">This function is not implemented.</span></span> <span data-ttu-id="41aa4-105">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="41aa4-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41aa4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41aa4-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41aa4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="41aa4-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="41aa4-108">[in] Ukazatel na počáteční umístění image uvolnit.</span><span class="sxs-lookup"><span data-stu-id="41aa4-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41aa4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41aa4-109">Requirements</span></span>  
 <span data-ttu-id="41aa4-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41aa4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41aa4-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41aa4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41aa4-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41aa4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41aa4-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41aa4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41aa4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41aa4-114">See also</span></span>
- [<span data-ttu-id="41aa4-115">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="41aa4-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
