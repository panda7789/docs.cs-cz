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
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762198"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="08edd-102">ICLRRuntimeInfo::IsStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="08edd-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="08edd-103">Určuje, zda byl modul runtime spuštěn (to znamená, zda byla volána [Metoda ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) a byla úspěšná).</span><span class="sxs-lookup"><span data-stu-id="08edd-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08edd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08edd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08edd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08edd-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="08edd-106">[out] `true` Pokud je tento modul runtime spuštěný; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="08edd-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="08edd-107">mimo Vrátí příznaky, které byly použity ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="08edd-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08edd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08edd-108">Return Value</span></span>  
 <span data-ttu-id="08edd-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="08edd-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="08edd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08edd-110">HRESULT</span></span>|<span data-ttu-id="08edd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="08edd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08edd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="08edd-112">S_OK</span></span>|<span data-ttu-id="08edd-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="08edd-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="08edd-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="08edd-114">E_NOTIMPL</span></span>|<span data-ttu-id="08edd-115">Verze modulu CLR (Common Language Runtime) je starší než verze CLR v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="08edd-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08edd-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08edd-116">Remarks</span></span>  
 <span data-ttu-id="08edd-117">Tato metoda nefunguje s verzemi CLR staršími než verze CLR v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="08edd-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08edd-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08edd-118">Requirements</span></span>  
 <span data-ttu-id="08edd-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08edd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08edd-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="08edd-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08edd-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08edd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08edd-122">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08edd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08edd-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="08edd-123">See also</span></span>

- [<span data-ttu-id="08edd-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08edd-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="08edd-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="08edd-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="08edd-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="08edd-126">Hosting</span></span>](index.md)
