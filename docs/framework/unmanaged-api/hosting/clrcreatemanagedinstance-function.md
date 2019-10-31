---
title: ClrCreateManagedInstance – funkce
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131988"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="ec919-102">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="ec919-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="ec919-103">Vytvoří instanci zadaného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="ec919-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="ec919-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec919-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ec919-105">Použijte aktivaci COM k vytvoření instance spravovaného typu nebo použijte hostování (viz [rozhraní pro hostování CLR přidaná v .NET Framework 4 a 4,5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="ec919-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec919-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec919-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec919-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec919-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="ec919-108">pro Ukazatel na název požadovaného typu instance.</span><span class="sxs-lookup"><span data-stu-id="ec919-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="ec919-109">pro `IID` požadovaného typu instance.</span><span class="sxs-lookup"><span data-stu-id="ec919-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="ec919-110">mimo Ukazatel na ukazatel na instanci spravovaného typu, který požadoval volající.</span><span class="sxs-lookup"><span data-stu-id="ec919-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec919-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec919-111">Remarks</span></span>  
 <span data-ttu-id="ec919-112">Modul CLR (Common Language Runtime) by již měl být načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="ec919-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="ec919-113">Například může být načten pomocí volání funkce [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) před voláním funkce `ClrCreateManagedInstance`.</span><span class="sxs-lookup"><span data-stu-id="ec919-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="ec919-114">Pokud modul runtime není načtený, `ClrCreateManagedInstance` se nejprve pokusí načíst v 1.0.3705 modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ec919-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="ec919-115">Pokud se to nepovede, pokusí se načíst nejnovější verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ec919-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec919-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec919-116">Requirements</span></span>  
 <span data-ttu-id="ec919-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec919-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec919-118">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec919-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec919-119">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec919-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec919-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec919-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec919-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec919-121">See also</span></span>

- [<span data-ttu-id="ec919-122">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ec919-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="ec919-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="ec919-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
