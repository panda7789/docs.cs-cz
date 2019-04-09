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
ms.openlocfilehash: 73a4a8a2fc737bbf4b49ca859f0549ca7efd54a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089767"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="44913-102">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="44913-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="44913-103">Vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="44913-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44913-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44913-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44913-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44913-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="44913-106">[in] Identifikátor rozhraní má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="44913-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="44913-107">[in] Ukazatel na uživatelské implementované [iclrdatatarget –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který představuje cílovou položku, pro který chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44913-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="44913-108">[out] Ukazatel na adresu objektu vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44913-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44913-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44913-109">Remarks</span></span>  
 <span data-ttu-id="44913-110">`ICLRDataTarget` Objektu je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="44913-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="44913-111">Implementace závisí na typu představované cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="44913-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="44913-112">Cílová položka může být proces, výpis paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="44913-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44913-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44913-113">Requirements</span></span>  
 <span data-ttu-id="44913-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44913-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44913-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="44913-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="44913-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44913-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="44913-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="44913-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44913-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44913-118">See also</span></span>

- [<span data-ttu-id="44913-119">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="44913-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
