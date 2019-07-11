---
title: ICLRMetaHost::EnumerateInstalledRuntimes – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b116a1f422daa20a2b51f0a5fc12d6065c2a01e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779806"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="279e0-102">ICLRMetaHost::EnumerateInstalledRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="279e0-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="279e0-103">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní pro jednotlivé verze common language runtime (CLR), který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="279e0-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="279e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="279e0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="279e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="279e0-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="279e0-106">[out] Výčet [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní odpovídající jednotlivým verzím modulu CLR, který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="279e0-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="279e0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="279e0-107">Return Value</span></span>  
 <span data-ttu-id="279e0-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="279e0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="279e0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="279e0-109">HRESULT</span></span>|<span data-ttu-id="279e0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="279e0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="279e0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="279e0-111">S_OK</span></span>|<span data-ttu-id="279e0-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="279e0-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="279e0-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="279e0-113">E_POINTER</span></span>|<span data-ttu-id="279e0-114">`ppEnumerator` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="279e0-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="279e0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="279e0-115">Requirements</span></span>  
 <span data-ttu-id="279e0-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="279e0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="279e0-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="279e0-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="279e0-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="279e0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="279e0-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="279e0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279e0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="279e0-120">See also</span></span>

- [<span data-ttu-id="279e0-121">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="279e0-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="279e0-122">Hostování</span><span class="sxs-lookup"><span data-stu-id="279e0-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
