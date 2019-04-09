---
title: ICorRuntimeHost::Start – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e6521f8013bf92f073ab4b6808871c95ac2802b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072854"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="e3a30-102">ICorRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="e3a30-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="e3a30-103">Spustí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e3a30-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3a30-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e3a30-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e3a30-105">Return Value</span></span>  
  
|<span data-ttu-id="e3a30-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3a30-106">HRESULT</span></span>|<span data-ttu-id="e3a30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a30-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3a30-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3a30-108">S_OK</span></span>|<span data-ttu-id="e3a30-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e3a30-109">The operation was successful.</span></span>|  
|<span data-ttu-id="e3a30-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e3a30-110">S_FALSE</span></span>|<span data-ttu-id="e3a30-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="e3a30-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e3a30-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3a30-112">E_FAIL</span></span>|<span data-ttu-id="e3a30-113">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e3a30-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e3a30-114">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="e3a30-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="e3a30-115">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3a30-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e3a30-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3a30-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3a30-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e3a30-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a30-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3a30-118">Remarks</span></span>  
 <span data-ttu-id="e3a30-119">Obvykle není nutné volat `Start` metody, protože modul CLR se spustí automaticky při první požadavek na spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e3a30-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a30-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3a30-120">Requirements</span></span>  
 <span data-ttu-id="e3a30-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a30-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a30-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3a30-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3a30-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3a30-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3a30-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e3a30-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a30-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a30-125">See also</span></span>

- [<span data-ttu-id="e3a30-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3a30-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
