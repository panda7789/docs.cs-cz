---
title: "PFN_CLRDataCreateInstance – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="16d16-102">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="16d16-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="16d16-103">Odkazuje na funkci, která vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="16d16-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16d16-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16d16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16d16-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="16d16-106">[v] Identifikátor rozhraní, které má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="16d16-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="16d16-107">[v] Ukazatel na uživatele implementované [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který reprezentuje cílová položka pro který chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16d16-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="16d16-108">[out] Ukazatel na adresu objekt vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16d16-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16d16-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16d16-109">Remarks</span></span>  
 <span data-ttu-id="16d16-110">`ICLRDataTarget` Objektu je implementováno modulem zapisovač ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="16d16-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="16d16-111">Implementace závisí na typu položky cíl reprezentované.</span><span class="sxs-lookup"><span data-stu-id="16d16-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="16d16-112">Cílová položka může být proces, výpis stavu paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="16d16-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d16-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16d16-113">Requirements</span></span>  
 <span data-ttu-id="16d16-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d16-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="16d16-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="16d16-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16d16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d16-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d16-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="16d16-118">See Also</span></span>  
 [<span data-ttu-id="16d16-119">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="16d16-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
