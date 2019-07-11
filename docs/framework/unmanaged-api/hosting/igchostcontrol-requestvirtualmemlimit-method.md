---
title: IGCHostControl::RequestVirtualMemLimit – metoda
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb0b6191c74c2b7ebdc8267701f246c17b016f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779529"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="f65ec-102">IGCHostControl::RequestVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="f65ec-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="f65ec-103">Požadavky hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="f65ec-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f65ec-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f65ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f65ec-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="f65ec-106">[in] Požadovaná velikost paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="f65ec-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="f65ec-107">[out v] Ukazatel na skutečnou velikost přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="f65ec-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f65ec-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f65ec-108">Requirements</span></span>  
 <span data-ttu-id="f65ec-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f65ec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f65ec-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f65ec-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f65ec-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f65ec-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f65ec-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f65ec-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f65ec-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f65ec-113">See also</span></span>

- [<span data-ttu-id="f65ec-114">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f65ec-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
