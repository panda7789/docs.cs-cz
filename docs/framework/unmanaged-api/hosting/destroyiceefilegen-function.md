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
ms.openlocfilehash: daf674c0340998c0fd518e0f1af721bbe9ff653c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490470"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="d7245-102">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="d7245-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="d7245-103">Zničí [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="d7245-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="d7245-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7245-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7245-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7245-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7245-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7245-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="d7245-107">[in] `ICeeFileGen` Objekt ke zničení.</span><span class="sxs-lookup"><span data-stu-id="d7245-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7245-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d7245-108">Return Value</span></span>  
 <span data-ttu-id="d7245-109">Tato metoda vrací standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="d7245-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7245-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7245-110">Remarks</span></span>  
 <span data-ttu-id="d7245-111">`DestroyICeeFileGen` Odstraní `ICeeFileGen` objekt vytvořený pomocí [createiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d7245-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7245-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7245-112">Requirements</span></span>  
 <span data-ttu-id="d7245-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7245-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7245-114">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="d7245-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="d7245-115">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="d7245-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="d7245-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7245-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7245-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7245-117">See also</span></span>

- [<span data-ttu-id="d7245-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="d7245-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
