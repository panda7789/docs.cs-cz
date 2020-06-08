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
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504014"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="b943f-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="b943f-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="b943f-103">Nastaví spouštěcí příznaky a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b943f-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="b943f-104">Tato metoda nahrazuje použití `startupFlags` parametru ve funkcích [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) a [CorBindToRuntimeHost –](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b943f-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b943f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b943f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b943f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b943f-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="b943f-107">pro Příznaky spuštění hostitele, které mají být nastaveny.</span><span class="sxs-lookup"><span data-stu-id="b943f-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="b943f-108">Používejte stejné příznaky jako s funkcemi [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) a [CorBindToRuntimeHost –](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b943f-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="b943f-109">pro Cesta k adresáři konfiguračního souboru hostitele, který se má nastavit.</span><span class="sxs-lookup"><span data-stu-id="b943f-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b943f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b943f-110">Return Value</span></span>  
 <span data-ttu-id="b943f-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="b943f-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b943f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b943f-112">HRESULT</span></span>|<span data-ttu-id="b943f-113">Description</span><span class="sxs-lookup"><span data-stu-id="b943f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b943f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b943f-114">S_OK</span></span>|<span data-ttu-id="b943f-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b943f-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b943f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b943f-116">Remarks</span></span>  
 <span data-ttu-id="b943f-117">Hostitel s více vlákny by měl synchronizovat volání této metody.</span><span class="sxs-lookup"><span data-stu-id="b943f-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="b943f-118">Jinak vlákno A může zavolat `SetStartupFlags` metodu poté, co vlákno b dokončí volání `SetStartupFlags` a před tím, než vlákno b spustí modul runtime.</span><span class="sxs-lookup"><span data-stu-id="b943f-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b943f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b943f-119">Requirements</span></span>  
 <span data-ttu-id="b943f-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b943f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b943f-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b943f-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b943f-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b943f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b943f-123">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b943f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b943f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b943f-124">See also</span></span>

- [<span data-ttu-id="b943f-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b943f-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b943f-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b943f-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b943f-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="b943f-127">Hosting</span></span>](index.md)
