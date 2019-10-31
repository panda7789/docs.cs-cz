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
ms.openlocfilehash: 30e3a88140c8a438001e8428df4c5ee879c83376
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136912"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="8a5be-102">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="8a5be-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="8a5be-103">Upozorní zavaděče na Nenačtené bitové kopie spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="8a5be-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="8a5be-104">Tato funkce není implementována.</span><span class="sxs-lookup"><span data-stu-id="8a5be-104">This function is not implemented.</span></span> <span data-ttu-id="8a5be-105">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8a5be-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a5be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a5be-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a5be-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a5be-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="8a5be-108">pro Ukazatel na počáteční umístění obrázku, který má být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="8a5be-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a5be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a5be-109">Requirements</span></span>  
 <span data-ttu-id="8a5be-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a5be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a5be-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a5be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a5be-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a5be-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a5be-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a5be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5be-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a5be-114">See also</span></span>

- [<span data-ttu-id="8a5be-115">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="8a5be-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
