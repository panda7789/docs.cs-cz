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
ms.openlocfilehash: 2df33e3edebbf558bf78986e737c4f7bb9b2f0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437154"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="903b1-102">IGCHostControl::RequestVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="903b1-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="903b1-103">Požadavky na hostiteli a změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="903b1-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="903b1-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="903b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="903b1-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="903b1-106">[v] Požadovaná velikost paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="903b1-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="903b1-107">[ve out] Ukazatel na skutečnou velikost přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="903b1-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="903b1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="903b1-108">Requirements</span></span>  
 <span data-ttu-id="903b1-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="903b1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="903b1-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="903b1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="903b1-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="903b1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="903b1-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="903b1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903b1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="903b1-113">See Also</span></span>  
 [<span data-ttu-id="903b1-114">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="903b1-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
