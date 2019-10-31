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
ms.openlocfilehash: 9415d5189edb901822abad9269e0150e7601a963
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140965"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="f5fef-102">ICLRMetaHost::EnumerateInstalledRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="f5fef-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="f5fef-103">Vrátí výčet obsahující platné rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pro každou verzi modulu CLR (Common Language Runtime), který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="f5fef-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5fef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5fef-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5fef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5fef-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="f5fef-106">mimo Výčet rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) odpovídajících každé verzi modulu CLR, která je nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="f5fef-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5fef-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5fef-107">Return Value</span></span>  
 <span data-ttu-id="f5fef-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="f5fef-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f5fef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5fef-109">HRESULT</span></span>|<span data-ttu-id="f5fef-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f5fef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5fef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5fef-111">S_OK</span></span>|<span data-ttu-id="f5fef-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f5fef-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5fef-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f5fef-113">E_POINTER</span></span>|<span data-ttu-id="f5fef-114">`ppEnumerator` je null.</span><span class="sxs-lookup"><span data-stu-id="f5fef-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5fef-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5fef-115">Requirements</span></span>  
 <span data-ttu-id="f5fef-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5fef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fef-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f5fef-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f5fef-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5fef-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5fef-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fef-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5fef-120">See also</span></span>

- [<span data-ttu-id="f5fef-121">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5fef-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="f5fef-122">Hostování</span><span class="sxs-lookup"><span data-stu-id="f5fef-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
