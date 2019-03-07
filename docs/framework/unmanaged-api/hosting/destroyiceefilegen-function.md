---
title: DestroyICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50bfe38bc4c4843ac0954a6c816e5dc06b5e0fed
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501952"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="7e0f4-102">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="7e0f4-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="7e0f4-103">Zničí [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="7e0f4-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="7e0f4-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e0f4-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e0f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e0f4-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e0f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e0f4-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="7e0f4-107">[in] `ICeeFileGen` Objekt ke zničení.</span><span class="sxs-lookup"><span data-stu-id="7e0f4-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e0f4-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7e0f4-108">Return Value</span></span>  
 <span data-ttu-id="7e0f4-109">Tato metoda vrací standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="7e0f4-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e0f4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e0f4-110">Remarks</span></span>  
 <span data-ttu-id="7e0f4-111">`DestroyICeeFileGen` Odstraní `ICeeFileGen` objekt vytvořený pomocí [createiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="7e0f4-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e0f4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e0f4-112">Requirements</span></span>  
 <span data-ttu-id="7e0f4-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e0f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0f4-114">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="7e0f4-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="7e0f4-115">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="7e0f4-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="7e0f4-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0f4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e0f4-117">See also</span></span>
- [<span data-ttu-id="7e0f4-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="7e0f4-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
