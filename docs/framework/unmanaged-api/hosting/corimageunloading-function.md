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
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178233"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="a7a19-102">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="a7a19-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="a7a19-103">Upozorní zavaděč při uvolnění bitové kopie spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="a7a19-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="a7a19-104">Tato funkce není implementována.</span><span class="sxs-lookup"><span data-stu-id="a7a19-104">This function is not implemented.</span></span> <span data-ttu-id="a7a19-105">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a7a19-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a19-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7a19-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a19-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7a19-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="a7a19-108">[v] Ukazatel na počáteční umístění obrázku k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="a7a19-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a19-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7a19-109">Requirements</span></span>  
 <span data-ttu-id="a7a19-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a19-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a19-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="a7a19-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7a19-112">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7a19-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7a19-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a19-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7a19-114">See also</span></span>

- [<span data-ttu-id="a7a19-115">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="a7a19-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
