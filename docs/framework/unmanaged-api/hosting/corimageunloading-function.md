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
ms.openlocfilehash: 585287f63f57f55e877c94684820833b6d1add60
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616535"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="59842-102">_CorImageUnloading – funkce</span><span class="sxs-lookup"><span data-stu-id="59842-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="59842-103">Upozorní zavaděče na Nenačtené bitové kopie spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="59842-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="59842-104">Tato funkce není implementována.</span><span class="sxs-lookup"><span data-stu-id="59842-104">This function is not implemented.</span></span> <span data-ttu-id="59842-105">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="59842-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59842-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59842-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59842-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="59842-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="59842-108">pro Ukazatel na počáteční umístění obrázku, který má být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="59842-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59842-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59842-109">Requirements</span></span>  
 <span data-ttu-id="59842-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59842-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59842-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="59842-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59842-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="59842-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59842-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59842-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59842-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="59842-114">See also</span></span>

- [<span data-ttu-id="59842-115">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="59842-115">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
