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
ms.openlocfilehash: d9d4965751db1a70871270317a644b0acb1302f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405977"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="a884a-102">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="a884a-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="a884a-103">Vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="a884a-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a884a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a884a-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a884a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a884a-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="a884a-106">[v] Identifikátor rozhraní, které má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="a884a-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="a884a-107">[v] Ukazatel na uživatele implementované [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objekt, který reprezentuje cílová položka pro který chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a884a-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="a884a-108">[out] Ukazatel na adresu objekt vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a884a-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a884a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a884a-109">Remarks</span></span>  
 <span data-ttu-id="a884a-110">`ICLRDataTarget` Objektu je implementováno modulem zapisovač ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a884a-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="a884a-111">Implementace závisí na typu položky cíl reprezentované.</span><span class="sxs-lookup"><span data-stu-id="a884a-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="a884a-112">Cílová položka může být proces, výpis stavu paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a884a-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a884a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a884a-113">Requirements</span></span>  
 <span data-ttu-id="a884a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a884a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a884a-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="a884a-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="a884a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a884a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a884a-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a884a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a884a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a884a-118">See Also</span></span>  
 [<span data-ttu-id="a884a-119">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="a884a-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
