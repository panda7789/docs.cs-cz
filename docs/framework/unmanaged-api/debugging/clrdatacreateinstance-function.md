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
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179366"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="a8575-102">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="a8575-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="a8575-103">Vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="a8575-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8575-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8575-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8575-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8575-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="a8575-106">[v] Identifikátor rozhraní, které má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="a8575-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="a8575-107">[v] Ukazatel na uživatelem implementovaný objekt [ICLRDataTarget,](iclrdatatarget-interface.md) který představuje cílovou položku, pro kterou chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8575-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="a8575-108">[out] Ukazatel na adresu vráceného objektu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8575-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8575-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8575-109">Remarks</span></span>  
 <span data-ttu-id="a8575-110">Objekt `ICLRDataTarget` je implementován zapisovače ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8575-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="a8575-111">Implementace závisí na typu reprezentované cílové položky.</span><span class="sxs-lookup"><span data-stu-id="a8575-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="a8575-112">Cílovou položkou může být proces, výpis stavu paměti, vzdálený počítač a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a8575-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8575-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8575-113">Requirements</span></span>  
 <span data-ttu-id="a8575-114">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8575-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8575-115">**Záhlaví:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="a8575-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="a8575-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8575-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8575-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8575-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8575-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8575-118">See also</span></span>

- [<span data-ttu-id="a8575-119">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="a8575-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
