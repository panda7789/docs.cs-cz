---
title: IApartmentCallback::DoCallback – metoda
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617110"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="09506-102">IApartmentCallback::DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="09506-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="09506-103">Spustí zadanou funkci v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="09506-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09506-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09506-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="09506-106">pro Ukazatel na funkci, která má být provedena v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="09506-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="09506-107">pro Ukazatel na argument funkce.</span><span class="sxs-lookup"><span data-stu-id="09506-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09506-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09506-108">Requirements</span></span>  
 <span data-ttu-id="09506-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09506-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09506-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09506-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09506-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="09506-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09506-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09506-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09506-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="09506-113">See also</span></span>

- [<span data-ttu-id="09506-114">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09506-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
