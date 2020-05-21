---
title: ICLRRuntimeInfo::SetDefaultStartupFlags – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: 7d201962976d198372226eb686696fcdccf3eb69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762159"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="12c0b-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="12c0b-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="12c0b-103">Nastaví spouštěcí příznaky a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="12c0b-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="12c0b-104">Tato metoda nahrazuje použití `startupFlags` parametru ve funkcích [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [CorBindToRuntimeHost –](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="12c0b-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c0b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c0b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12c0b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="12c0b-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="12c0b-107">pro Příznaky spuštění hostitele, které mají být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="12c0b-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="12c0b-108">Používejte stejné příznaky jako s funkcemi [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [CorBindToRuntimeHost –](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="12c0b-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="12c0b-109">pro Cesta k adresáři konfiguračního souboru hostitele, který se má nastavit.</span><span class="sxs-lookup"><span data-stu-id="12c0b-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12c0b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12c0b-110">Return Value</span></span>  
 <span data-ttu-id="12c0b-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="12c0b-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="12c0b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12c0b-112">HRESULT</span></span>|<span data-ttu-id="12c0b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="12c0b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12c0b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="12c0b-114">S_OK</span></span>|<span data-ttu-id="12c0b-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="12c0b-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12c0b-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12c0b-116">Remarks</span></span>  
 <span data-ttu-id="12c0b-117">Hostitel s více vlákny by měl synchronizovat volání této metody.</span><span class="sxs-lookup"><span data-stu-id="12c0b-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="12c0b-118">Jinak vlákno A může zavolat `SetStartupFlags` metodu poté, co vlákno b dokončí volání `SetStartupFlags` a před tím, než vlákno b spustí modul runtime.</span><span class="sxs-lookup"><span data-stu-id="12c0b-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c0b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12c0b-119">Requirements</span></span>  
 <span data-ttu-id="12c0b-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c0b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c0b-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="12c0b-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="12c0b-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12c0b-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12c0b-123">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12c0b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c0b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="12c0b-124">See also</span></span>

- [<span data-ttu-id="12c0b-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12c0b-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="12c0b-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="12c0b-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="12c0b-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="12c0b-127">Hosting</span></span>](index.md)
