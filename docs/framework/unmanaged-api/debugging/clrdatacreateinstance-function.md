---
title: CLRDataCreateInstance – funkce
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a839eb2edd36dc726c819a819fd4d427fbaea40
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740991"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="72438-102">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="72438-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="72438-103">Vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="72438-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72438-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72438-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72438-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="72438-106">[in] Identifikátor rozhraní má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="72438-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="72438-107">[in] Ukazatel na uživatelské implementované [iclrdatatarget –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který představuje cílovou položku, pro který chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72438-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="72438-108">[out] Ukazatel na adresu objektu vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72438-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72438-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72438-109">Remarks</span></span>  
 <span data-ttu-id="72438-110">`ICLRDataTarget` Objektu je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="72438-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="72438-111">Implementace závisí na typu představované cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="72438-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="72438-112">Cílová položka může být proces, výpis paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="72438-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72438-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72438-113">Requirements</span></span>  
 <span data-ttu-id="72438-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72438-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72438-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="72438-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="72438-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72438-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72438-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72438-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72438-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72438-118">See also</span></span>

- [<span data-ttu-id="72438-119">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="72438-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
