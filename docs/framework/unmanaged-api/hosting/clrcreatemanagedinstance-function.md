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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176536"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="f6324-102">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="f6324-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="f6324-103">Vytvoří instanci zadaného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f6324-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="f6324-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f6324-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="f6324-105">Pomocí aktivace com vytvořte instanci spravovaného typu nebo použijte hostování (viz [CLR Hosting Interfaces Added in .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="f6324-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6324-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6324-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6324-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6324-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="f6324-108">[v] Ukazatel na název požadovaného typu instance.</span><span class="sxs-lookup"><span data-stu-id="f6324-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="f6324-109">[v] Požadovaný `IID` typ instance.</span><span class="sxs-lookup"><span data-stu-id="f6324-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f6324-110">[out] Ukazatel na ukazatel na instanci spravovaného typu, který byl požadován volajícím.</span><span class="sxs-lookup"><span data-stu-id="f6324-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6324-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6324-111">Remarks</span></span>  
 <span data-ttu-id="f6324-112">Běžný jazyk runtime by již měla být načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="f6324-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="f6324-113">Například může být načten pomocí volání funkce [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `ClrCreateManagedInstance` před voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="f6324-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="f6324-114">Pokud není načten za `ClrCreateManagedInstance` běhu, nejprve se pokusí načíst v1.0.3705 runtime.</span><span class="sxs-lookup"><span data-stu-id="f6324-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="f6324-115">Pokud se to nezdaří, pokusí se načíst nejnovější verzi za běhu.</span><span class="sxs-lookup"><span data-stu-id="f6324-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6324-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6324-116">Requirements</span></span>  
 <span data-ttu-id="f6324-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6324-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6324-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6324-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6324-119">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6324-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6324-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6324-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6324-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6324-121">See also</span></span>

- [<span data-ttu-id="f6324-122">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f6324-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="f6324-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="f6324-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
