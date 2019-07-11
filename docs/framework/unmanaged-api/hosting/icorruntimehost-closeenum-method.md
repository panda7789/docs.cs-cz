---
title: ICorRuntimeHost::CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfddd1d8f6fed105224cb2294d68f3f0bc016403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762161"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="9af75-102">ICorRuntimeHost::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="9af75-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="9af75-103">Obnoví domény enumerátor zpět na začátek seznamu domén.</span><span class="sxs-lookup"><span data-stu-id="9af75-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9af75-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9af75-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9af75-106">[in] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="9af75-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9af75-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9af75-107">Return Value</span></span>  
  
|<span data-ttu-id="9af75-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9af75-108">HRESULT</span></span>|<span data-ttu-id="9af75-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9af75-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9af75-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9af75-110">S_OK</span></span>|<span data-ttu-id="9af75-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9af75-111">The operation was successful.</span></span>|  
|<span data-ttu-id="9af75-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9af75-112">S_FALSE</span></span>|<span data-ttu-id="9af75-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="9af75-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9af75-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9af75-114">E_FAIL</span></span>|<span data-ttu-id="9af75-115">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="9af75-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9af75-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="9af75-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9af75-117">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9af75-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9af75-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9af75-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9af75-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9af75-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9af75-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9af75-120">Requirements</span></span>  
 <span data-ttu-id="9af75-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af75-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af75-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9af75-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9af75-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9af75-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9af75-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9af75-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af75-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9af75-125">See also</span></span>

- [<span data-ttu-id="9af75-126">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9af75-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9af75-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9af75-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
