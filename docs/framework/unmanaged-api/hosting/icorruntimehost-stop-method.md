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
ms.openlocfilehash: 3c59a0c5ef1e89c2853a566bd3b587d15a1ed80c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119259"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="62f52-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="62f52-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="62f52-103">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="62f52-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62f52-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="62f52-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62f52-105">Return Value</span></span>  
  
|<span data-ttu-id="62f52-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62f52-106">HRESULT</span></span>|<span data-ttu-id="62f52-107">Popis</span><span class="sxs-lookup"><span data-stu-id="62f52-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62f52-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="62f52-108">S_OK</span></span>|<span data-ttu-id="62f52-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="62f52-109">The operation was successful.</span></span>|  
|<span data-ttu-id="62f52-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="62f52-110">S_FALSE</span></span>|<span data-ttu-id="62f52-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="62f52-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="62f52-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62f52-112">E_FAIL</span></span>|<span data-ttu-id="62f52-113">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="62f52-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="62f52-114">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="62f52-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="62f52-115">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62f52-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="62f52-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62f52-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62f52-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="62f52-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62f52-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62f52-118">Remarks</span></span>  
 <span data-ttu-id="62f52-119">Je obvykle zbytečné volání `Stop` metody, protože kód se zastaví provádění při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="62f52-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62f52-120">Po volání `Stop`, modul CLR nelze ho inicializovat znovu ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="62f52-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f52-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62f52-121">Requirements</span></span>  
 <span data-ttu-id="62f52-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f52-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f52-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62f52-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62f52-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62f52-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62f52-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="62f52-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f52-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62f52-126">See also</span></span>

- [<span data-ttu-id="62f52-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62f52-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
