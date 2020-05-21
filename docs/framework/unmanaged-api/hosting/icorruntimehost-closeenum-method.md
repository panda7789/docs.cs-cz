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
ms.openlocfilehash: a5a86df3ac1f50ca624490ad80a6fed903433436
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762367"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="28936-102">ICorRuntimeHost::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="28936-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="28936-103">Obnoví enumerátor domény zpátky na začátek seznamu domén.</span><span class="sxs-lookup"><span data-stu-id="28936-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28936-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28936-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28936-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28936-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="28936-106">pro Enumerátor, který má být resetován.</span><span class="sxs-lookup"><span data-stu-id="28936-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28936-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="28936-107">Return Value</span></span>  
  
|<span data-ttu-id="28936-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28936-108">HRESULT</span></span>|<span data-ttu-id="28936-109">Popis</span><span class="sxs-lookup"><span data-stu-id="28936-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28936-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="28936-110">S_OK</span></span>|<span data-ttu-id="28936-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="28936-111">The operation was successful.</span></span>|  
|<span data-ttu-id="28936-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="28936-112">S_FALSE</span></span>|<span data-ttu-id="28936-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="28936-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="28936-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28936-114">E_FAIL</span></span>|<span data-ttu-id="28936-115">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="28936-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="28936-116">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="28936-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="28936-117">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28936-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28936-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28936-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28936-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="28936-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28936-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28936-120">Requirements</span></span>  
 <span data-ttu-id="28936-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28936-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28936-122">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="28936-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28936-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="28936-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28936-124">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="28936-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28936-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="28936-125">See also</span></span>

- [<span data-ttu-id="28936-126">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="28936-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="28936-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28936-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
