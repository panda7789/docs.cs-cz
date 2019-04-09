---
title: CreateICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151811"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="b33c3-102">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="b33c3-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="b33c3-103">Vytvoří [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b33c3-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="b33c3-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b33c3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b33c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b33c3-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b33c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b33c3-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="b33c3-107">[out] Ukazatel na novou adresu `ICeeFileGen` objektu.</span><span class="sxs-lookup"><span data-stu-id="b33c3-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b33c3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b33c3-108">Return Value</span></span>  
 <span data-ttu-id="b33c3-109">Tato metoda vrací standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="b33c3-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b33c3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b33c3-110">Remarks</span></span>  
 <span data-ttu-id="b33c3-111">`ICeeFileGen` Objektu se používá k vytvoření common language runtime (CLR) souborů (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="b33c3-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="b33c3-112">Volání [destroyiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkce zrušení `ICeeFileGen` objekt po dokončení.</span><span class="sxs-lookup"><span data-stu-id="b33c3-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b33c3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b33c3-113">Requirements</span></span>  
 <span data-ttu-id="b33c3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b33c3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b33c3-115">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="b33c3-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="b33c3-116">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="b33c3-116">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="b33c3-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b33c3-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b33c3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b33c3-118">See also</span></span>

- [<span data-ttu-id="b33c3-119">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="b33c3-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
