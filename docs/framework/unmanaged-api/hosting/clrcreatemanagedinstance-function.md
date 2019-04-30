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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789620"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="f78e8-102">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="f78e8-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="f78e8-103">Vytvoří instanci určeného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f78e8-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="f78e8-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f78e8-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="f78e8-105">Použít aktivaci modelu COM. k vytvoření instance spravovaného typu, nebo použít hostování (viz [CLR hostování rozhraní přidaná v rozhraní .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="f78e8-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78e8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f78e8-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f78e8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f78e8-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="f78e8-108">[in] Ukazatel na název požadovaného typu instance.</span><span class="sxs-lookup"><span data-stu-id="f78e8-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="f78e8-109">[in] `IID` Typu instanci požaduje.</span><span class="sxs-lookup"><span data-stu-id="f78e8-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f78e8-110">[out] Ukazatel na ukazatel na instanci spravovaného typu, který byl vyžádán volajícím.</span><span class="sxs-lookup"><span data-stu-id="f78e8-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f78e8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f78e8-111">Remarks</span></span>  
 <span data-ttu-id="f78e8-112">Modul common language runtime by již načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="f78e8-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="f78e8-113">Například můžete načíst pomocí volání [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fungovaly před `ClrCreateManagedInstance` funkce je volána.</span><span class="sxs-lookup"><span data-stu-id="f78e8-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="f78e8-114">Pokud není načten modul runtime, `ClrCreateManagedInstance` poprvé pokusí se načíst v1.0.3705 modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f78e8-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="f78e8-115">Pokud selže, pokusí se načíst nejnovější verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f78e8-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f78e8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f78e8-116">Requirements</span></span>  
 <span data-ttu-id="f78e8-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f78e8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f78e8-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f78e8-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f78e8-119">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f78e8-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f78e8-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f78e8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78e8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f78e8-121">See also</span></span>

- [<span data-ttu-id="f78e8-122">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f78e8-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="f78e8-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="f78e8-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
