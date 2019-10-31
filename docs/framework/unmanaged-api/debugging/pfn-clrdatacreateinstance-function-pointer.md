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
ms.openlocfilehash: 426a8acf2e9319725cf592db00dc97c8960bca4f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139171"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="1f6a7-102">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="1f6a7-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="1f6a7-103">Odkazuje na funkci, která vytvoří objekt rozhraní pro zadanou cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f6a7-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f6a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f6a7-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="1f6a7-106">pro Identifikátor rozhraní, které má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="1f6a7-107">pro Ukazatel na uživatelem implementovaný objekt [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) , který představuje cílovou položku, pro kterou chcete vytvořit objekt rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="1f6a7-108">mimo Ukazatel na adresu vráceného objektu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6a7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f6a7-109">Remarks</span></span>  
 <span data-ttu-id="1f6a7-110">Objekt `ICLRDataTarget` je implementován modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="1f6a7-111">Implementace závisí na typu reprezentované cílové položky.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="1f6a7-112">Cílová položka může být proces, výpis paměti, vzdálený počítač atd.</span><span class="sxs-lookup"><span data-stu-id="1f6a7-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6a7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f6a7-113">Requirements</span></span>  
 <span data-ttu-id="1f6a7-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f6a7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6a7-115">**Hlavička:** ClrData. idl</span><span class="sxs-lookup"><span data-stu-id="1f6a7-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="1f6a7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1f6a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f6a7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6a7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f6a7-118">See also</span></span>

- [<span data-ttu-id="1f6a7-119">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="1f6a7-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
