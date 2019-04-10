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
ms.openlocfilehash: 37ff40e1c009b8e1e0509a4a3333d5a2a70bbfd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159884"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="81ff6-102">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="81ff6-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="81ff6-103">Zničí [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="81ff6-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="81ff6-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81ff6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ff6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81ff6-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81ff6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="81ff6-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="81ff6-107">[in] `ICeeFileGen` Objekt ke zničení.</span><span class="sxs-lookup"><span data-stu-id="81ff6-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81ff6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81ff6-108">Return Value</span></span>  
 <span data-ttu-id="81ff6-109">Tato metoda vrací standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="81ff6-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81ff6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81ff6-110">Remarks</span></span>  
 `DestroyICeeFileGen` <span data-ttu-id="81ff6-111">Odstraní `ICeeFileGen` objekt vytvořený pomocí [createiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="81ff6-111">destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ff6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81ff6-112">Requirements</span></span>  
 <span data-ttu-id="81ff6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ff6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ff6-114">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="81ff6-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="81ff6-115">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="81ff6-115">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="81ff6-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="81ff6-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81ff6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81ff6-117">See also</span></span>

- [<span data-ttu-id="81ff6-118">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="81ff6-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
