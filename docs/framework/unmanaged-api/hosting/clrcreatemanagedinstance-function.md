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
ms.openlocfilehash: ecd618ecf08836ea5e38ce738f97fc91ee6426f4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616809"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="30495-102">ClrCreateManagedInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="30495-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="30495-103">Vytvoří instanci zadaného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="30495-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="30495-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="30495-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="30495-105">Použijte aktivaci COM k vytvoření instance spravovaného typu nebo použijte hostování (viz [rozhraní pro hostování CLR přidaná v .NET Framework 4 a 4,5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="30495-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30495-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30495-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30495-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="30495-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="30495-108">pro Ukazatel na název požadovaného typu instance.</span><span class="sxs-lookup"><span data-stu-id="30495-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="30495-109">pro Požadovaný `IID` typ instance.</span><span class="sxs-lookup"><span data-stu-id="30495-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="30495-110">mimo Ukazatel na ukazatel na instanci spravovaného typu, který požadoval volající.</span><span class="sxs-lookup"><span data-stu-id="30495-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30495-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30495-111">Remarks</span></span>  
 <span data-ttu-id="30495-112">Modul CLR (Common Language Runtime) by již měl být načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="30495-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="30495-113">Například může být načten pomocí volání funkce [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) před `ClrCreateManagedInstance` voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="30495-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="30495-114">Pokud modul runtime není načtený, `ClrCreateManagedInstance` nejprve se pokusí načíst v 1.0.3705 modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="30495-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="30495-115">Pokud se to nepovede, pokusí se načíst nejnovější verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="30495-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30495-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30495-116">Requirements</span></span>  
 <span data-ttu-id="30495-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30495-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30495-118">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30495-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30495-119">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="30495-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30495-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30495-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30495-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="30495-121">See also</span></span>

- [<span data-ttu-id="30495-122">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="30495-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="30495-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="30495-123">Hosting</span></span>](index.md)
