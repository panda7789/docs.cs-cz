---
title: ICorRuntimeHost::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1af01559e65bd80fc62cb2eba44bf21d4fa3113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770906"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="1ea18-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="1ea18-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="1ea18-103">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="1ea18-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ea18-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1ea18-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ea18-105">Return Value</span></span>  
  
|<span data-ttu-id="1ea18-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ea18-106">HRESULT</span></span>|<span data-ttu-id="1ea18-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1ea18-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ea18-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ea18-108">S_OK</span></span>|<span data-ttu-id="1ea18-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1ea18-109">The operation was successful.</span></span>|  
|<span data-ttu-id="1ea18-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1ea18-110">S_FALSE</span></span>|<span data-ttu-id="1ea18-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="1ea18-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1ea18-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ea18-112">E_FAIL</span></span>|<span data-ttu-id="1ea18-113">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1ea18-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1ea18-114">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="1ea18-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1ea18-115">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ea18-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ea18-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ea18-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ea18-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1ea18-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ea18-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ea18-118">Remarks</span></span>  
 <span data-ttu-id="1ea18-119">Je obvykle zbytečné volání `Stop` metody, protože kód se zastaví provádění při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="1ea18-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ea18-120">Po volání `Stop`, modul CLR nelze ho inicializovat znovu ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="1ea18-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea18-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ea18-121">Requirements</span></span>  
 <span data-ttu-id="1ea18-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea18-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea18-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ea18-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ea18-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ea18-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea18-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1ea18-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea18-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ea18-126">See also</span></span>

- [<span data-ttu-id="1ea18-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ea18-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
