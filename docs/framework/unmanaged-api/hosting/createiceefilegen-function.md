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
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136821"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="8bd10-102">CreateICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="8bd10-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="8bd10-103">Vytvoří objekt [ICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="8bd10-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="8bd10-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8bd10-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd10-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bd10-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bd10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bd10-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="8bd10-107">mimo Ukazatel na adresu nového objektu `ICeeFileGen`.</span><span class="sxs-lookup"><span data-stu-id="8bd10-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bd10-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bd10-108">Return Value</span></span>  
 <span data-ttu-id="8bd10-109">Tato metoda vrátí standardní kódy chyb modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8bd10-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd10-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bd10-110">Remarks</span></span>  
 <span data-ttu-id="8bd10-111">Objekt `ICeeFileGen` slouží k vytvoření přenosných spustitelných souborů (PE) pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8bd10-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="8bd10-112">Po dokončení volejte funkci [DestroyICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) pro zničení objektu `ICeeFileGen`.</span><span class="sxs-lookup"><span data-stu-id="8bd10-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd10-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bd10-113">Requirements</span></span>  
 <span data-ttu-id="8bd10-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd10-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd10-115">**Hlavička:** ICeeFileGen –. h</span><span class="sxs-lookup"><span data-stu-id="8bd10-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="8bd10-116">**Knihovna:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="8bd10-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="8bd10-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd10-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bd10-118">See also</span></span>

- [<span data-ttu-id="8bd10-119">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="8bd10-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
