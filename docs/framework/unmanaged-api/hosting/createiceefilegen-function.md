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
ms.openlocfilehash: bc98641085591feaaa5c97c7ee04885ef79d39f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429434"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="60057-102">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="60057-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="60057-103">Vytvoří [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="60057-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="60057-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60057-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60057-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60057-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60057-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="60057-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="60057-107">[out] Ukazatel na adresu nového `ICeeFileGen` objektu.</span><span class="sxs-lookup"><span data-stu-id="60057-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60057-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60057-108">Return Value</span></span>  
 <span data-ttu-id="60057-109">Tato metoda vrátí standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="60057-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60057-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60057-110">Remarks</span></span>  
 <span data-ttu-id="60057-111">`ICeeFileGen` Objekt se používá k vytvoření common language runtime (CLR) přenosné spustitelný soubor (PE) souborů.</span><span class="sxs-lookup"><span data-stu-id="60057-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="60057-112">Volání [destroyiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkce zrušení `ICeeFileGen` objektu po dokončení.</span><span class="sxs-lookup"><span data-stu-id="60057-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60057-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60057-113">Requirements</span></span>  
 <span data-ttu-id="60057-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60057-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60057-115">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="60057-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="60057-116">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="60057-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="60057-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60057-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60057-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="60057-118">See Also</span></span>  
 [<span data-ttu-id="60057-119">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="60057-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
