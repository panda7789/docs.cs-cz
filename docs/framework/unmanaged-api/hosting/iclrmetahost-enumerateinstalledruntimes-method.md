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
ms.openlocfilehash: c99607bfe5fda01eb1abfd7771cb3907ddabeec5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703773"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="090c8-102">ICLRMetaHost::EnumerateInstalledRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="090c8-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="090c8-103">Vrátí výčet obsahující platné rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) pro každou verzi modulu CLR (Common Language Runtime), který je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="090c8-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="090c8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="090c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="090c8-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="090c8-106">mimo Výčet rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) odpovídajících každé verzi modulu CLR, která je nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="090c8-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="090c8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="090c8-107">Return Value</span></span>  
 <span data-ttu-id="090c8-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="090c8-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="090c8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="090c8-109">HRESULT</span></span>|<span data-ttu-id="090c8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="090c8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="090c8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="090c8-111">S_OK</span></span>|<span data-ttu-id="090c8-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="090c8-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="090c8-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="090c8-113">E_POINTER</span></span>|<span data-ttu-id="090c8-114">`ppEnumerator`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="090c8-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="090c8-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="090c8-115">Requirements</span></span>  
 <span data-ttu-id="090c8-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="090c8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="090c8-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="090c8-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="090c8-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="090c8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="090c8-119">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="090c8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090c8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="090c8-120">See also</span></span>

- [<span data-ttu-id="090c8-121">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="090c8-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="090c8-122">Hostování</span><span class="sxs-lookup"><span data-stu-id="090c8-122">Hosting</span></span>](index.md)
