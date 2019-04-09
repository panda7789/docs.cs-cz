---
title: PFN_CLRDataCreateInstance – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff2ddb1e98f3455c6915acf8149f528176228425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177980"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="0f39f-102">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="0f39f-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="0f39f-103">Odkazuje na funkci, která vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="0f39f-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f39f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f39f-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f39f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f39f-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="0f39f-106">[in] Identifikátor rozhraní má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="0f39f-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="0f39f-107">[in] Ukazatel na uživatelské implementované [iclrdatatarget –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který představuje cílovou položku, pro který chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f39f-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="0f39f-108">[out] Ukazatel na adresu objektu vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f39f-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f39f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f39f-109">Remarks</span></span>  
 <span data-ttu-id="0f39f-110">`ICLRDataTarget` Objektu je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f39f-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="0f39f-111">Implementace závisí na typu představované cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="0f39f-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="0f39f-112">Cílová položka může být proces, výpis paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0f39f-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f39f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f39f-113">Requirements</span></span>  
 <span data-ttu-id="0f39f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f39f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f39f-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="0f39f-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="0f39f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f39f-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0f39f-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0f39f-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0f39f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f39f-118">See also</span></span>

- [<span data-ttu-id="0f39f-119">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="0f39f-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
