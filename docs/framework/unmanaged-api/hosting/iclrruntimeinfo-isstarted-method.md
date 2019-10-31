---
title: ICLRRuntimeInfo::IsStarted – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 34590744407b25d7d53c06c452fff5bac2a95246
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136387"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="f12bd-102">ICLRRuntimeInfo::IsStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f12bd-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="f12bd-103">Určuje, zda byl modul runtime spuštěn (to znamená, zda byla volána [Metoda ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) a byla úspěšná).</span><span class="sxs-lookup"><span data-stu-id="f12bd-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f12bd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f12bd-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="f12bd-106">[out] `true`, pokud je spuštěn tento modul runtime; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f12bd-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="f12bd-107">mimo Vrátí příznaky, které byly použity ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f12bd-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f12bd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f12bd-108">Return Value</span></span>  
 <span data-ttu-id="f12bd-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="f12bd-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f12bd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f12bd-110">HRESULT</span></span>|<span data-ttu-id="f12bd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f12bd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f12bd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f12bd-112">S_OK</span></span>|<span data-ttu-id="f12bd-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f12bd-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f12bd-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f12bd-114">E_NOTIMPL</span></span>|<span data-ttu-id="f12bd-115">Verze modulu CLR (Common Language Runtime) je starší než verze CLR v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f12bd-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f12bd-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f12bd-116">Remarks</span></span>  
 <span data-ttu-id="f12bd-117">Tato metoda nefunguje s verzemi CLR staršími než verze CLR v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f12bd-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12bd-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f12bd-118">Requirements</span></span>  
 <span data-ttu-id="f12bd-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12bd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12bd-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f12bd-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f12bd-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f12bd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f12bd-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12bd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12bd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f12bd-123">See also</span></span>

- [<span data-ttu-id="f12bd-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f12bd-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f12bd-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f12bd-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f12bd-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="f12bd-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
