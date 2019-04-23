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
ms.openlocfilehash: f150fe80302cd03e872ca8bdf5d172caae1ce599
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230769"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="9499e-102">ICorRuntimeHost::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="9499e-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="9499e-103">Obnoví domény enumerátor zpět na začátek seznamu domén.</span><span class="sxs-lookup"><span data-stu-id="9499e-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9499e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9499e-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9499e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9499e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9499e-106">[in] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="9499e-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9499e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9499e-107">Return Value</span></span>  
  
|<span data-ttu-id="9499e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9499e-108">HRESULT</span></span>|<span data-ttu-id="9499e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9499e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9499e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9499e-110">S_OK</span></span>|<span data-ttu-id="9499e-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9499e-111">The operation was successful.</span></span>|  
|<span data-ttu-id="9499e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9499e-112">S_FALSE</span></span>|<span data-ttu-id="9499e-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="9499e-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9499e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9499e-114">E_FAIL</span></span>|<span data-ttu-id="9499e-115">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="9499e-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9499e-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="9499e-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9499e-117">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9499e-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9499e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9499e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9499e-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9499e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9499e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9499e-120">Requirements</span></span>  
 <span data-ttu-id="9499e-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9499e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9499e-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9499e-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9499e-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9499e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9499e-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9499e-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9499e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9499e-125">See also</span></span>

- [<span data-ttu-id="9499e-126">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9499e-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9499e-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9499e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
